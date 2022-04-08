Get the top 10 contributors based on IP and URI for all the blocked requests. 
We need to monitor httpRequest.clientIp and httpRequest.uri for requests where action = “BLOCK”.

For Log format, choose JSON.
Under Contribution→ keys, enter a contributor type httpRequest.clientIp and httpRequest.uri
Under Contributions → Filters use the following.  
      a.	Match → Action
      b.	Condition → In
      c.	Value  → BLOCK
For Aggregation → Aggregate on, choose COUNT
