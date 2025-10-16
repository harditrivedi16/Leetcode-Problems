---
id: 1af7e332-de10-806e-9e9d-fa95ff43876f
title: Target Sum
created_time: 2025-03-07T16:23:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/target-sum/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Dynamic Programming
companies_asked:
  - Google
  - Amazon
  - Microsoft
  - Facebook/Meta
  - Myntra
  - Pinterest
problem_name: Target Sum

---

```python
from typing import List

class Solution:
    def countSubsetSum(self, nums: List[int], k: int) -> int:
        n = len(nums)
        t = [[0] * (k + 1) for _ in range(n + 1)]

        # If sum is 0, there is always one way (by selecting an empty subset)
        for i in range(n + 1): 
            t[i][0] = 1  

        for i in range(1, n + 1): 
            for j in range(k + 1):  
                if nums[i - 1] <= j:
                    t[i][j] = t[i - 1][j] + t[i - 1][j - nums[i - 1]]
                else:
                    t[i][j] = t[i - 1][j]

        return t[n][k]

    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        totalSum = sum(nums)

        # If (target + totalSum) is odd or target is out of range
        if (target + totalSum) % 2 != 0 or totalSum < abs(target):  
            return 0  

        k = (target + totalSum) // 2

        # Standard subset sum count multiplied by 2^zero_count to account for ±0 choices
        return self.countSubsetSum(nums, k) 


```

## Time Complexity

O(n \* sum), where n is the length of the input array nums and sum is the total sum of all elements in nums.

This is because we create a DP table of size (n+1) × (sum+1) and fill each cell exactly once.

## Space Complexity

O(n \* sum), where n is the length of the input array nums and sum is the total sum of all elements in nums.

This space is used to store the dynamic programming table t\[]\[] of size (n+1) × (k+1), where k is (target + totalSum) / 2.
