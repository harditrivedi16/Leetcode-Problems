---
id: 14b7e332-de10-806d-a8f3-d55581def06d
title: Meeting Rooms
created_time: 2024-11-27T22:36:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Leetcode Curated Algorithms
  - Neetcode - 150
  - Blind 75
problem_link: https://leetcode.com/problems/meeting-rooms/description/
my_confidence_level: High
number: 33
last_solved: 2024-11-28T00:00:00.000Z
concept_involved:
  - Intervals
companies_asked:
  - TicTok
  - Facebook/Meta
  - Amazon
problem_name: Meeting Rooms

---

```python
class Solution:
    def canAttendMeetings(self, intervals: List[List[int]]) -> bool:

        intervals.sort(key = lambda i: i[0])
        for i in range(len(intervals)): 
            if i + 1 < len(intervals) and intervals[i][1] > intervals[i+1][0]:  
                return False
        return True
        
```

Time Complexity: O(n) as it goes through each element of the list

Space Complexity: O(1)
