---
id: 1317e332-de10-8116-af35-f39aff794f24
title: 'Non - Overlapping Interval '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:14:00.000Z
difficulty_level: 'Meduim '
number: 29
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Blind 75
problem_link: https://leetcode.com/problems/non-overlapping-intervals/
my_confidence_level: Meduim
last_solved: 2025-10-15T00:00:00.000Z
concept_involved:
  - Intervals
companies_asked:
  - Microsoft
  - Zoho
problem_name: 'Non - Overlapping Interval '

---

```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:

        intervals.sort(key = lambda i : i[0])
        
        res = 0 

        for i in range(len(intervals)): 
            if i + 1 < len(intervals) and intervals[i][1] > intervals[i+1][0]: 
                res+=1 
                intervals[i+1][1] = min(intervals[i][1],intervals[i+1][1])
        return res
```

This solution removes the minimum number of overlapping intervals by sorting them by start time and counting overlaps, adjusting the end times to preserve as many non-overlapping intervals as possible.

**Time Complexity**: O(n log n), where n is the number of intervals, due to sorting.
**Space Complexity**: O(1), as the algorithm modifies the intervals in place and uses a constant amount of extra space.
