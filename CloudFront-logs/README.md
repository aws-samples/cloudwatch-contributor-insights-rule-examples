## Cloudwatch Contributor Insights Rule Examples for CloudFront standard access logs

This Repo contains sample CloudWatch Contributor Insight Rules for CloudFront standard access logs.
Each File in this repo represents a rule definition as a CloudFormation Resource, as well as the JSON representation of the Rule definition.


#### CF-Bytes-Out-By-POP ####

This rule tracks the number of bytes sent out by each CloudFront edge location. This can help you view which edge location is responsible for serving the majority of traffic over time.


#### CF-Cache-Miss-by-URI ####

This rule shows you the top requested URIs that resulted in a cache miss. The rule is filtered for only GET and HEAD requests, because PUT, POST, and DELETE requests cannot result in a cache hit. This rule is helpful for identifying objects that might be good candidates for caching.



#### CF-Edge-Status-by-POP ####

This rule shows you the edge status for each request by edge location. This can be helpful to identify which edge locations are producing the most errors or miss or hit requests.



#### CF-Errors-By-POP-and-Path ####

This rule shows you the top contributors for errors by URI path and edge location. This can be helpful for identifying which URI or edge location is responsible for a higher than expected error rate



#### CF-Requests-by-HTTP-Method ####

This rule displays the total number of requests by the HTTP method used (GET, POST, PUT, OPTIONS, HEAD, DELETE). This can help you get a better understanding of the type of requests that are being made to your distribution. You can gather this same data point by using a CloudWatch Logs metric filter.



#### CF-Requests-by-URI ####

This rule shows you the top requested URIs across your CloudFront distribution over time.


#### CF-Requests-by-URI-and-UserAgent ####

A modification of the previous rule, this rule tracks the top requests by URI and the User Agent field. This rule can help you understand if some objects are more requested by different user agents.


#### CF-Status-by-POP ####

This rule tracks the HTTP response codes by CloudFront edge location. This can help you see which edge locations are producing the most requests that result in an error or a 200 OK.



## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License Summary

The documentation is made available under the Creative Commons Attribution-ShareAlike 4.0 International License. See the LICENSE file.

The sample code within this documentation is made available under the MIT-0 license. See the LICENSE-SAMPLECODE file.
