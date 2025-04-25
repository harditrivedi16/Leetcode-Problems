---
id: 1907e332-de10-802c-9b55-f182d2fa031e
title: Maximum Ascending Subarray Sum
created_time: 2025-02-04T16:50:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/maximum-ascending-subarray-sum/
my_confidence_level: Meduim
number: 59
amazon_prep: 'No'
last_solved: 2025-02-04T00:00:00.000Z
concept_involved:
  - Arrays
  - PrefixSum
companies_asked:
  - Tcs
problem_name: Maximum Ascending Subarray Sum

---

```python
from typing import List

class Solution:
    def maxAscendingSum(self, nums: List[int]) -> int:
        max_sum = nums[0]  # Store the maximum sum found
        curr_sum = nums[0]  # Track the current ascending sum

        for i in range(1, len(nums)):
            if nums[i] > nums[i - 1]:  # Continue increasing sequence
                curr_sum += nums[i]
            else:  # Reset sum for a new sequence
                max_sum = max(max_sum, curr_sum)
                curr_sum = nums[i]

        return max(max_sum, curr_sum)  # Ensure the last sequence is considered

```

Time Comp: O(n)
Space Comp: O(1)
