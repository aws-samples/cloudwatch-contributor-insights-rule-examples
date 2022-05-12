# Cloudwatch Contributor Insights Rule Examples for AWS WAF  logs

This Repo contains sample CloudWatch Contributor Insight Rules for AWS WAF  logs. Each File in this repo represents a rule definition as a CloudFormation Resource, as well as the JSON representation of the Rule definition.

**Get the Top ten Terminating Rules:** get the top ten terminating rule ids

**Get the top ten IP addresses, URI combination for all the Blocked requests:**  Get the top 10 contributors based on IP and URI for all the blocked requests. We need to monitor httpRequest.clientIp and httpRequest.uri for requests where action = “BLOCK”.

**Get the top ten rules within the Rule group that Blocked or Counted**:XX

**Top ten IP addresses blocked by rate-based rules**:xx 
