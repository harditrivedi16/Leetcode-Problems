---
id: 2177e332-de10-80de-b363-d6f7acb4594f
title: Jump Game
created_time: 2025-06-19T15:19:00.000Z
last_edited_time: 2025-06-21T19:46:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-06-19T00:00:00.000Z
concept_involved: []
companies_asked: []
problem_name: Jump Game

---

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
