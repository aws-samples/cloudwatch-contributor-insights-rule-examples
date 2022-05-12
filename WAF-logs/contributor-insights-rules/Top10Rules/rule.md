With Contributor Insight, Rules you cannot automatically iterate through all array elements to find all matching contributors.  
However, we can write a rule for a specific element in the array. Since the order of the rules in the Rule Group is pre known you can write one rule per Rule Group to display the rules within the Rule Groups that got triggered.

To do that you will need to monitor  
$.ruleGroupList[1].terminatingRule.ruleId"

In addition I’ve used $.ruleGroupList[1].terminatingRule.action"
which indicates whether the traffic is Blocked or Counted by the particular rule.

For Log format, choose JSON.
Under Contribution→ keys, enter a contributor type
      a.	ruleGroupList[1].terminatingRule.ruleId
      b.	ruleGroupList[1].terminatingRule.action
For Aggregation → Aggregate on, choose COUNT

Repeat this to add the Rule groups in your WebACL

