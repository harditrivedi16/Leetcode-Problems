---
id: 2177e332-de10-80a5-aa8d-f1890be41b5b
title: 'Jump Game II '
created_time: 2025-06-19T16:05:00.000Z
last_edited_time: 2025-06-22T14:26:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
number: null
june_interviews_prep: null
last_solved: 2025-06-19T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: 'Jump Game II '

---

**Problem Statement:**

Given the same setup (array `nums`, where `nums[i]` = max jump length from index `i`), **find the minimum number of jumps** needed to reach the last index.

**Return:** The **minimum number of jumps** required.

```java
class Solution(object):
    def jump(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        jumps = 0 
        l , r = 0, 0 
        farthest = 0
        while r < len(nums) - 1: 
            
            for i in range(l, r + 1): 
                farthest = max(farthest, i + nums[i])
            
            l = r + 1 
            r = farthest
            jumps += 1
        return jumps
        
```
