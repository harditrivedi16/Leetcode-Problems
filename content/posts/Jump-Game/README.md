---
id: 2177e332-de10-80de-b363-d6f7acb4594f
title: Jump Game
created_time: 2025-06-19T15:19:00.000Z
last_edited_time: 2025-06-22T14:25:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-06-19T00:00:00.000Z
concept_involved: []
companies_asked: []
problem_name: Jump Game

---

Given an array `nums` where `nums[i]` represents the **maximum number of steps** you can jump forward from index `i`, determine **if you can reach the last index** starting from index 0.

**Return:** `True` if reachable, otherwise `False`.

```java
class Solution(object):
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        goal = len(nums) - 1

        for i in range(len(nums) - 1, -1, -1 ): 
            if i + nums[i] >= goal: 
                goal = i
        return True if goal == 0 else False
        
```

O(n), 1,
