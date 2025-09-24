---
id: 1e37e332-de10-802c-aa22-d8fce3f0a466
title: Palindrome Partitioning
created_time: 2025-04-28T15:16:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Dynamic Programming
companies_asked: []
problem_name: Palindrome Partitioning

---

```python
import sys

def is_palindrome(s, i, j):
    while i < j:
        if s[i] != s[j]:
            return False
        i += 1
        j -= 1
    return True

def palindrome_partition(s):
    n = len(s)
    dp = [[-1] * n for _ in range(n)]
    return min_cuts(s, 0, n - 1, dp)

def min_cuts(s, i, j, dp):
    if i >= j or is_palindrome(s, i, j):
        return 0
    if dp[i][j] != -1:
        return dp[i][j]

    min_cut = sys.maxsize
    for k in range(i, j):
        if is_palindrome(s, i, k):  # Only cut if left part is a palindrome
            right = min_cuts(s, k + 1, j, dp)
            min_cut = min(min_cut, 1 + right)

    dp[i][j] = min_cut
    return dp[i][j]
```

### Problem Statement:

Given a string `s`, partition it into the **fewest number of cuts** such that **every substring** in the partition is a **palindrome**.

Return the **minimum number of cuts** needed.

### Intuition (MCM Pattern):

This is a classic **"partition DP"** problem, very similar to **Matrix Chain Multiplication (MCM)**.

We try to partition the string at every position `k` between `i` and `j` and recursively solve the subproblems.

The key observations are:

*   If the substring from `i` to `j` is already a palindrome, then **no cut is needed**.

*   Otherwise, we try all possible partitions (`k`) and calculate:

    *   `1 + minCuts(left) + minCuts(right)`

*   The `is_palindrome(i, j)` check is reused using a helper.

We store already computed results in a DP table `dp[i][j]` to avoid recomputation.

### Time Complexity:

*   Worst case: **O(n³)**

    *   `O(n²)` states (i, j)

    *   `O(n)` for the loop inside each state to try all `k`

Let me know if you want the optimized version using a precomputed palindrome table.
