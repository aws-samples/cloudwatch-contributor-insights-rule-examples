## Top 10 contributors based on IP and URI for all the blocked requests

Get the top 10 contributors based on IP and URI for all the blocked requests. 
We need to monitor httpRequest.clientIp and httpRequest.uri for requests where action = “BLOCK”.

1. For Log format, choose JSON.
2. Under Contribution→ keys, enter a contributor type httpRequest.clientIp and httpRequest.uri
3. Under Contributions → Filters use the following.  
      1. Match → Action
      2. Condition → In
      3. Value  → BLOCK
4. For Aggregation → Aggregate on, choose COUNT
