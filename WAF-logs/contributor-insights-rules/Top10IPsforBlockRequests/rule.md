## Top 10 contributors based on IP and URI for all the blocked requests

Get the top 10 contributors based on IP and URI for all the blocked requests. 
We need to monitor httpRequest.clientIp and httpRequest.uri for requests where action = “BLOCK”.

For Log format, choose JSON.
1. Under Contribution→ keys, enter a contributor type httpRequest.clientIp and httpRequest.uri
2. Under Contributions → Filters use the following.  
      1. Match → Action
      2. Condition → In
      3. Value  → BLOCK
3. For Aggregation → Aggregate on, choose COUNT
