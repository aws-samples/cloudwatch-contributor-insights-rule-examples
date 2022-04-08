Top 100 IP addresses blocked by rate-based rules. This is useful to identify the top talkers to your application.  
This data can help you identify legitimate traffic versus unwanted bot traffic. 
For example, this can help you gauge whether or not you want to adjust your rate-based rule thresholds if legitimate clients are being blocked improperly.

For Log format, choose JSON.
Under Contribution→ keys, enter a contributor type httpRequest.clientIp
Under Contributions → Filters use the following.  
a.	Match → terminatingRuleType
b.	Condition → In
c.	Value → RATE_BASED
For Aggregation → Aggregate on, choose COUNT