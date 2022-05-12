## Top 10 contributors based on IP and URI for all the blocked requests

Get the top 10 contributors based on IP and URI for all the blocked requests. 
We need to monitor httpRequest.clientIp and httpRequest.uri for requests where action = “BLOCK”.

For Log format, choose JSON.
Under Contribution→ keys, enter a contributor type httpRequest.clientIp and httpRequest.uri
Under Contributions → Filters use the following.  
      1. Match → Action
      2. Condition → In
      3. Value  → BLOCK
For Aggregation → Aggregate on, choose COUNT
