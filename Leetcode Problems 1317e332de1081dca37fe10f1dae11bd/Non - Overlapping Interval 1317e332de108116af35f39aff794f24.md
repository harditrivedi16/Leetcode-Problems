# Non - Overlapping Interval

Companies asked : Microsoft, Zoho
Concept involved: Intervals
Difficulty level: Meduim 
Last Solved : October 10, 2024
Leetcode Problem List: Blind 75, Neetcode - 150
My Confidence Level : Meduim
Number: 18
Problem Link: https://leetcode.com/problems/non-overlapping-intervals/

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