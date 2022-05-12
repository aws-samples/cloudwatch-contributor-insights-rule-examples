# Cloudwatch Contributor Insights Rule Examples for AWS WAF  logs

This repo contains sample CloudWatch Contributor Insight Rules for AWS WAF  logs. Each File in this repo represents a rule definition as a CloudFormation Resource, as well as the JSON representation of the Rule definition.

**Get the Top ten Terminating Rules:** 

Get the top ten terminating rule ids. We need to monitor terminatingRuleId

**Get the top ten IP addresses, URI combination for all the Blocked requests:**  

Get the top 10 contributors based on IP and URI for all the blocked requests. We need to monitor httpRequest.clientIp and httpRequest.uri for requests where action = “BLOCK”.

**Get the top ten rules within the Rule group that Blocked or Counted**:

With Contributor Insight, Rules you cannot automatically iterate through all array elements to find all matching contributors.
However, we can write a rule for a specific element in the array. Since the order of the rules in the Rule Group is pre known you can write one rule per Rule Group to display the rules within the Rule Groups that got triggered.

To do that you will need to monitor
$.ruleGroupList[1].terminatingRule.ruleId"

In addition I’ve used $.ruleGroupList[1].terminatingRule.action" which indicates whether the traffic is Blocked or Counted by the particular rule.i

**Top ten IP addresses blocked by rate-based rules**:

Top 100 IP addresses blocked by rate-based rules. This is useful to identify the top talkers to your application.
This data can help you identify legitimate traffic versus unwanted bot traffic. For example, this can help you gauge whether or not you want to adjust your rate-based rule thresholds if legitimate clients are being blocked improperly.
