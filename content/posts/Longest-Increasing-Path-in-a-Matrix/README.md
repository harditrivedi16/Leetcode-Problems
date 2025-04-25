---
id: 17e7e332-de10-8034-8105-d43b0d3c96cd
title: Longest Increasing Path in a Matrix
created_time: 2025-01-17T20:22:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/longest-increasing-path-in-a-matrix/
my_confidence_level: Meduim
number: 55
amazon_prep: 'No'
last_solved: 2025-01-17T00:00:00.000Z
concept_involved:
  - DFS
  - Graphs
  - Dynamic Programming
companies_asked:
  - Facebook/Meta
  - DoorDash
  - TicTok
  - Google
  - WeRide
problem_name: Longest Increasing Path in a Matrix

---

```python
class Solution:
    def longestIncreasingPath(self, matrix: List[List[int]]) -> int:

        ROWS, COLS = len(matrix), len(matrix[0])
        dp = {} 

        def dfs(r, c, prevValue): 

            if (r < 0 or r >= ROWS or 
                c < 0 or c >= COLS or
                matrix[r][c] <= prevValue): 
                return 0
            
            if (r,c) in dp: 
                return dp[(r,c)]
            
            res = 1 
            res = max(res, 1 + dfs(r + 1, c, matrix[r][c]))
            res = max(res, 1 + dfs(r - 1, c, matrix[r][c]))
            res = max(res, 1 + dfs(r, c + 1, matrix[r][c]))
            res = max(res, 1 + dfs(r, c - 1, matrix[r][c]))

            dp[(r,c)] = res

            return res

        for r in range(ROWS): 
            for c in range(COLS):
                dfs(r, c, -1)
        return max(dp.values())
```

Time Complexity: O(m\*n)

Space complexity: O(m\*n)
