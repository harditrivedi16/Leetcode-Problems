---
id: 17e7e332-de10-80d8-9143-ec9db76c2ed5
title: Pacific Atlantic Water Flow
created_time: 2025-01-17T20:24:00.000Z
last_edited_time: 2025-10-15T18:10:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/pacific-atlantic-water-flow/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - DFS
  - Graphs
companies_asked:
  - Google
  - Amazon
  - Facebook/Meta
problem_name: Pacific Atlantic Water Flow

---

```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        ROWS, COLS = len(heights), len(heights[0])

        pac, atl = set(), set()

        def dfs(r, c, visit, prevValue) -> None: 

            if (r < 0 or r >= ROWS or 
                c < 0 or c >= COLS or 
                heights[r][c] < prevValue or 
                (r, c) in visit): 
                return
            visit.add((r,c))

            dfs(r + 1, c, visit, heights[r][c])
            dfs(r - 1, c, visit, heights[r][c])
            dfs(r, c + 1, visit, heights[r][c])
            dfs(r, c - 1, visit, heights[r][c])
    
        for c in range(COLS): 
            dfs(0, c, pac, heights[0][c])
            dfs(ROWS - 1, c, atl, heights[ROWS -1][c])
        for r in range(ROWS): 
            dfs(r, 0, pac, heights[r][0])
            dfs(r, COLS - 1, atl, heights[r][COLS - 1])
        
        res = []
        for r in range(ROWS):
            for c in range(COLS): 
                if (r,c) in pac and (r,c) in atl: 
                    res.append([r,c])
        return res

```

### **Summary:**

*   **Time Complexity:** `O(m * n)`

*   **Space Complexity:** `O(m * n)`
