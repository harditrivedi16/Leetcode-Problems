---
id: 14b7e332-de10-806d-a8f3-d55581def06d
title: Meeting Rooms
created_time: 2024-11-27T22:36:00.000Z
last_edited_time: 2025-10-15T18:14:00.000Z
difficulty_level: Easy
number: 30
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Leetcode Curated Algorithms
  - Neetcode - 150
  - Blind 75
problem_link: https://leetcode.com/problems/meeting-rooms/description/
my_confidence_level: High
last_solved: 2025-10-15T00:00:00.000Z
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

**Java Code:**

```java
import java.util.*;

class Solution {
    public boolean canAttendMeetings(int[][] intervals) {
        if (intervals.length == 0) return true;

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] < intervals[i - 1][1]) {
                return false;
            }
        }

        return true;
    }
}

```

Time Complexity: O(n) as it goes through each element of the list

Space Complexity: O(1)
