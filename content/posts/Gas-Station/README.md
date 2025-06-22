---
id: 2177e332-de10-8033-8750-f9e6343dcc3d
title: Gas Station
created_time: 2025-06-19T16:05:00.000Z
last_edited_time: 2025-06-21T19:46:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-06-21T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Gas Station

---

```python
class Solution(object):
    def canCompleteCircuit(self, gas, cost):
        """
        :type gas: List[int]
        :type cost: List[int]
        :rtype: int
        """
        if sum(gas) < sum(cost):
            return -1

        total = 0
        res = 0
        for i in range(len(gas)):
            total += (gas[i] - cost[i])

            if total < 0:
                total = 0
                res = i + 1
        
        return res
```
