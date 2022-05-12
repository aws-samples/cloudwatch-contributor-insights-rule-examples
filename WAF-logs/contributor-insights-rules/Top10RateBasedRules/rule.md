Top 100 IP addresses blocked by rate-based rules. This is useful to identify the top talkers to your application.  
This data can help you identify legitimate traffic versus unwanted bot traffic. 
For example, this can help you gauge whether or not you want to adjust your rate-based rule thresholds if legitimate clients are being blocked improperly.

1. For Log format, choose JSON.
2. Under Contribution→ keys, enter a contributor type httpRequest.clientIp
3. Under Contributions → Filters use the following.  
    1. Match → terminatingRuleType
    2. Condition → In
    3. Value → RATE_BASED
4. For Aggregation → Aggregate on, choose COUNT
