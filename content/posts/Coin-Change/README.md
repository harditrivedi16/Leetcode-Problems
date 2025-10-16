---
id: 1bc7e332-de10-80ee-b426-f79d6abc4d0d
title: Coin Change
created_time: 2025-03-20T16:22:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
  - Top Interview Questions
problem_link: https://leetcode.com/problems/coin-change/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Dynamic Programming
companies_asked:
  - Amazon
  - Uber
  - Google
  - Bloomberg
  - Geico
  - paypal
  - Microsoft
  - TicTok
  - Walmart
problem_name: Coin Change

---

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        n = len(coins)
        W = amount
        INT_MAX = sys.maxsize
       # Initialize DP table
        t = [[0 if j == 0 else INT_MAX - 1 for j in range(W + 1)] for i in range(n + 1)]

        # Base condition: If either no items or capacity is 0
        for j in range(1, W + 1):
            if j % coins[0] == 0:
                t[1][j] = j // coins[0]
            else:
                t[1][j] = INT_MAX - 1
        # Filling DP table
        for i in range(1, n + 1):
            for j in range(1, W + 1):
                if coins[i - 1] <= j:
                    t[i][j] = min(t[i][j - coins[i - 1]] + 1, t[i - 1][j])
                else:
                    t[i][j] = t[i - 1][j]

        return -1 if t[n][W] == INT_MAX - 1 else t[n][W]
```
