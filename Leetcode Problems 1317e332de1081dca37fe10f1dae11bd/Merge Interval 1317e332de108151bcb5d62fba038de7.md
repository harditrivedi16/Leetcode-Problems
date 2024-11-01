# Merge Interval

Companies asked : Amazon, Apple, Bloomberg, Facebook/Meta, Google, Grammarly, Microsoft, Oracle, TicTok
Concept involved: Intervals
Difficulty level: Meduim 
Last Solved : October 10, 2024
Leetcode Problem List: Blind 75, Neetcode - 150, Top 100 Liked Questions, Top Facebook Questions, Top Microsoft Questions
My Confidence Level : Meduim
Number: 17
Problem Link: https://leetcode.com/problems/merge-intervals/description/

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