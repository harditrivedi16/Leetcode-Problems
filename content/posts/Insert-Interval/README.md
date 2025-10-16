---
id: 1317e332-de10-81cf-8556-e924a747da1f
title: Insert Interval
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:14:00.000Z
difficulty_level: 'Meduim '
number: 27
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Blind 75
problem_link: https://leetcode.com/problems/insert-interval/
my_confidence_level: High
last_solved: 2025-10-15T00:00:00.000Z
concept_involved:
  - Intervals
companies_asked:
  - Google
  - Facebook/Meta
  - Linkedin
problem_name: Insert Interval

---

**Python Code:**

```python
class Solution: 
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]: 

        res = [] 

        for i in range(len(intervals)): 
            if newInterval[1] < intervals[i][0]:
                res.append(newInterval)
                return res + intervals[i:]
            elif newInterval[0]> intervals[i][1]: 
                res.append(intervals[i])
            else: 
                newInterval = [min(newInterval[0], intervals[i][0]),max(newInterval[1], intervals[i][1])] 
            
        res.append(newInterval)

        return res
        

```

**Time Complexity**: O(n), where n is the number of intervals, as it processes each interval once.
**Space Complexity**: O(n), as it stores the resulting list of intervals.
