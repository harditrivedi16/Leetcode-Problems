---
id: 1bb7e332-de10-80a3-a5af-d5782366ee52
title: Coin Change II
created_time: 2025-03-19T13:56:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/coin-change-ii/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Dynamic Programming
companies_asked:
  - Google
  - Microsoft
  - Amazon
problem_name: Coin Change II

---

```python
class Solution:
    def change(self, amount: int, coins: List[int]) -> int:
        # Initialize DP table
        n = len(coins)
        W = amount
        t = [[0] * (W + 1) for _ in range(n + 1)]

        # Base condition: If either no items or capacity is 0
        for i in range(n+1):
                t[i][0] = 1

        # Filling DP table
        for i in range(1, n + 1):
            for j in range(1, W + 1):
                if coins[i - 1] <= j:
                    t[i][j] = t[i][j - coins[i - 1]] + t[i - 1][j]
                else:
                    t[i][j] = t[i - 1][j]

        return t[n][W]

                
```
