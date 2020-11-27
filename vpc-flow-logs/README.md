## Cloudwatch Contributor Insights Rule Examples for VPC Flow Logs

This Repo contains sample CloudWatch Contributor Insight Rules for VPC Flow Logs.
Each File in this repo represents a rule definition as a CloudFormation Resource, as well as the JSON representation of the Rule definition.


**Note:** VPC Flow Logs support [adding additional metadata to log entries!](https://aws.amazon.com/blogs/aws/learn-from-your-vpc-flow-logs-with-additional-meta-data/), such as VPC Id, Instance Id, as well as TCP flags.  The order of fields in VPC Flow Logs can be customized. CloudWatch Insight Rules are built by matching the field position in the log event with the name of the field or alias. In the default VPC Flow Logging format the position of the *< interface-id >* field would be 3. However this may not be the case if a customized logging format is used.
Keeping track of the position of a given field in a log format is important, since we need to use these positions when defining an Insight Rule. All of the example rules in this repo use the default VPC Flow logging format. For example If we would like to track the Top-N contributors for the number of bytes transferred by unique source IP addresses, we would need to the position of the *<bytes>* field, as well as the position of the *<srcaddr>* field. In the default VPC Flow Logging format, *<srcaddr>* maps to position 4, and *<bytes>* maps to position 10.

### Using an Insights Rule to evaluate many VPC Flow Log Groups: ###
A Contributor Insight Rule is applied to one or many Log Groups. This allows customers to have a single Contributor Insights rule apply to VPC Flow Logs for an entire AWS Account in a given region or across an organization in a given region if Flow Logs are sent to Log Groups in a centralized account
If we assume that all of our VPC Flow Logs share a prefix name in CloudWatch Logs. Such as */vpc/flowlogs/*, we can have a rule apply to every CloudWatch Log Group that shares this prefix name. By using a wildcard expression, we can have a single Insight Rule apply to many CloudWatch Log Groups
This is valuable, because we are able to use a single rule to track Top-N contributors across all of our VPCs in a given region. For example we can track the Top-N contributors by aggregating the number of rejected request by source IP and destination port. We can add additional contributors to show top rejected requests by source IP, destination port, as well as Interface ID, or subnet ID.


#### Top-SSH-by-action-and-source-IP ####

This rule will show us the Top-N contributors by source and IP for connections over port 22. However this rule can be modified to show denied actions for any port number.


#### Top-Rejected-SSH-by-source-IP ####

This rule can show us only rejected actions over port 22, as well as track the Top-N contributors by source  IP address. We can accomplish this by modifying the filters to filter for port 22, and an action of Reject. In addition to this, we can modify the rule further to display the Top-N contributors by rejected action on port 22, by source and destination address.



#### Accepts vs Rejects by VPC or Subnet ID ####

If we configured our VPC Flow logs to track either subnet-id, or vpc-id, we can track Accepts-vs-Rejects by VPC, or Subnet. In this example we have added additional metadata to our VPC Flow Logs, so that the ‘vpc-id’ field maps to position 25 in the log format, and the ‘subnet-id’ field maps to position 22 in the log format. We can also track overall accepts vs rejects by removing the 'vpc-id', or 'subnet-id' fields. we can also calculate this by using metrics emitted from the following Insight Rules:
* Traffic by Source Address and Rejected Action
* Traffic by Source Address and Action

 Details on this method can be found here - ( link to blog post )



#### Rejects by port and Source IP ####

When analyzing VPC Flow Logs from a security lens, it is helpful to be able to identify what connections are being rejected, by port and source IP address. The rule example in this repo provides the Top-N contributors by Source IP address and port where the action was rejected. This can give us an overall picture of what source IPs are responsible for the majority of rejected connections, and what ports they are attempting to make these connections on.



#### Top Contributors for Establishing Requests ####

We can use the TCP flags field to determine which source IPs initiated the most TCP connections.
For this rule, we will want to track the Source IP address, as well as values where the tcp-flag is. In VPC Flow Logs the TCP Flags can be aggregated in the same line for short connections, so there are a few values we will need to track to show connections established by source IP.
* 2 – for a SYN
* 3 – SYN and FIN on the same line
* 19 – SYN, SYN-ACK, and FIN on the same line
We can modify this rule in a few ways to show us a different dimension of this data. For example, we could add destination address, or destination port as a contributor in addition to the source address. This would now tell us who is making the most requests to source IPs and ports.



#### Requests by TCP Flag ####

TCP flags are one of the additional metadata fields that can be added to VPC Flow Logs. In the example in this repo, we have the ‘tcp-flag’ field mapped to position 23 in the VPC Flow Log format.
The rule will display the bitmask for TCP Flags observed within the aggregation period. For example, FIN is 0x01 (1), SYN is 0x02 (2), ACK is 0x10 (16), SYN + ACK is 0x12 (18), etc. (the bits are specified in “Control Bits” section of RFC793 “Transmission Control Protocol Specification”).


#### Bytes Transferred by VPC or Subnet ID ####

The Following Rule syntax will provide the Top-N VPCs that generate the most traffic in terms of bytes transferred for all VPC Flow Logs whose Log Group Name starts with /vpc/flowlogs/*. In this example we have added additional metadata to the VPC Flow Logs, so that the ‘vpc-id’ field maps to position 25 in the log format, and the ‘subnet-id’ field maps to position 22 in the  log format.
To modify this rule to show the top contributors in data transferred by ‘subnet-id’ instead of ‘vpc-id’. This can be done by replacing ‘vpc-id’ with ‘subnet-id’ in the ‘Keys’ array in the rule body
`
    "Contribution": {
        "Filters": [],
        "Keys": [
            "subnet-id"
        ],
        "ValueOf": "bytes"
    }
 `


#### Accepts by destination port and Subnet ID ####

In this example we have added additional metadata to our VPC Flow Logs, so that the ‘vpc-id’ field maps to position 25 in the log format, and the ‘subnet-id’ field maps to position 22 in the log format. The rule shown in this repo will track the Top-N contributors  for accepted requests by destination port and Subnet ID. However we can modify this rule in several ways. For example we could update it to track the Top-N contributors by vpc-id instead, or track destination IP instead of destination port.




## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License Summary

The documentation is made available under the Creative Commons Attribution-ShareAlike 4.0 International License. See the LICENSE file.

The sample code within this documentation is made available under the MIT-0 license. See the LICENSE-SAMPLECODE file.
