# Insert Interval

Companies asked : Facebook/Meta, Google, Linkedin
Concept involved: Intervals
Difficulty level: Meduim 
Last Solved : October 10, 2024
Leetcode Problem List: Blind 75, Neetcode - 150
My Confidence Level : Meduim
Number: 16
Problem Link: https://leetcode.com/problems/insert-interval/

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

This solution merges a new interval into a list of non-overlapping intervals by iterating through the existing intervals, adding those that don't overlap, and merging those that do.

**Time Complexity**: O(n), where n is the number of intervals, as it processes each interval once.
**Space Complexity**: O(n), as it stores the resulting list of intervals.