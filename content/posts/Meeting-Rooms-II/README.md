---
id: 18e7e332-de10-8044-8cf9-dada86b71f87
title: Meeting Rooms II
created_time: 2025-02-02T19:12:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Leetcode Curated Algorithms
  - Top Amazon Questions
  - Top Google Questions
  - Top Interview Questions
  - Top Microsoft Questions
problem_link: https://leetcode.com/problems/meeting-rooms-ii/
my_confidence_level: Meduim
number: 57
amazon_prep: 'No'
last_solved: 2025-02-02T00:00:00.000Z
concept_involved:
  - Intervals
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
  - TicTok
  - Bloomberg
  - Netflix
  - Microsoft
  - Apple
  - Salesforce
  - Hubspot
problem_name: Meeting Rooms II

---

```python
class Solution:
    def minMeetingRooms(self, intervals: List[List[int]]) -> int:

        start = sorted([i[0] for i in intervals])
        end = sorted([i[1] for i in intervals])

        s, e = 0, 0 
        res, count = 0, 0

        while s < len(start): 
            if start[s] < end[e]: 
                s += 1
                count += 1
            else: 
                e += 1
                count -= 1
            res = max(res, count)
        return res
```

# **Time & Space Complexity**

**Time complexity: O(nlog⁡n)*****O*****(*****n*****log*****n*****)Space complexity: O(n)*****O*****(*****n*****)**

*   Time complexity: *O*(*n\_log\_n*)

    **O(nlog⁡n)**

*   Space complexity: *O*(*n*)

    **O(n)**
