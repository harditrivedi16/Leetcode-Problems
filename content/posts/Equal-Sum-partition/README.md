---
id: 1ae7e332-de10-8031-9ad6-f2d709e63382
title: Equal Sum partition
created_time: 2025-03-06T23:11:00.000Z
last_edited_time: 2025-10-15T18:10:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
problem_link: https://leetcode.com/problems/partition-equal-subset-sum/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Dynamic Programming
companies_asked:
  - Facebook/Meta
  - Bloomberg
  - Microsoft
  - Amazon
  - TicTok
  - Google
problem_name: Equal Sum partition

---

```python
from typing import List

class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        total_sum = sum(nums)

        # If total sum is odd, we cannot partition it into two equal subsets
        if total_sum % 2 != 0:
            return False

        target = total_sum // 2
        n = len(nums)

        # DP table: t[i][j] = True if we can form sum 'j' using first 'i' elements
        t = [[False] * (target + 1) for _ in range(n + 1)]

        # Base condition: If sum is 0, it's always possible (empty subset)
        for i in range(n + 1):
            t[i][0] = True

        # Fill DP table
        for i in range(1, n + 1):
            for j in range(1, target + 1):
                if nums[i - 1] <= j:
                    t[i][j] = t[i - 1][j] or t[i - 1][j - nums[i - 1]]
                else:
                    t[i][j] = t[i - 1][j]

        return t[n][target]
```

*   **Time Complexity**: `O(n * target)`, where `target = total_sum / 2`.

*   **Space Complexity**: `O(n * target)`, but it can be optimized to `O(target)` using a **1D array**.
