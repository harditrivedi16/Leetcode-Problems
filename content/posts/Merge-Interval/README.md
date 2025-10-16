---
id: 1317e332-de10-8151-bcb5-d62fba038de7
title: Merge Interval
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:14:00.000Z
difficulty_level: 'Meduim '
number: 28
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
  - Top Facebook Questions
  - Top Microsoft Questions
  - Blind 75
problem_link: https://leetcode.com/problems/merge-intervals/description/
my_confidence_level: Meduim
last_solved: 2025-10-15T00:00:00.000Z
concept_involved:
  - Intervals
companies_asked:
  - Facebook/Meta
  - Amazon
  - Google
  - Microsoft
  - Apple
  - Bloomberg
  - TicTok
  - Grammarly
  - Oracle
problem_name: Merge Interval

---

**Python Code:**

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        res = []

        intervals.sort(key = lambda i : i[0])

        for i in range(len(intervals)): 
            if (i+1 < len(intervals)) and (intervals[i][1]  >= intervals[i+1][0]): 
                intervals[i+1] = [min(intervals[i][0], intervals[i+1][0]), max(intervals[i][1], intervals[i+1][1])]
            else: 
                res.append(intervals[i])
        return res
```

This solution merges overlapping intervals by sorting them based on their start times and then merging any consecutive intervals that overlap.

**Time Complexity**: O(n log n), where n is the number of intervals, due to sorting.
**Space Complexity**: O(n), as it stores the merged intervals in the result list.
