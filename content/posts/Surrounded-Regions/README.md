---
id: 1767e332-de10-804e-8376-e1140c38be5f
title: Surrounded Regions
created_time: 2025-01-09T01:16:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top Interview Questions
problem_link: https://leetcode.com/problems/surrounded-regions/description/
my_confidence_level: Meduim
number: 51
amazon_prep: 'No'
last_solved: 2025-01-16T00:00:00.000Z
concept_involved:
  - BFS
  - Graphs
  - DFS
companies_asked:
  - Google
  - Amazon
  - Facebook/Meta
problem_name: Surrounded Regions

---

```python
from collections import deque

class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """

        rows, cols = len(board), len(board[0])
        visit = set()

        def dfs(r,c): 
            if r < 0 or r >= rows or c < 0 or c >= cols or board[r][c]!= 'O' or (r,c) in visit: 
                return 
            visit.add((r,c))

            dfs(r + 1, c)
            dfs(r - 1, c)
            dfs(r, c + 1)
            dfs(r, c - 1) 




        def bfs(r,c): 
            q = deque()
            q.append((r,c))
            visit.add((r,c))
            

            while q: 
                row, col = q.popleft()
                directions = [[1,0], [-1,0], [0,1], [0,-1]]
                for dr, dc in directions: 
                    r = row + dr
                    c = col + dc

                    if r in range(rows) and c in range(cols) and board[r][c] == 'O' and (r,c) not in visit:
                        
                        q.append((r,c))
                        visit.add((r,c)) 

        for r in range(rows): 
            if board[r][0] == 'O' and (r, 0) not in visit:  # Left edge
                dfs(r, 0)
                #bfs(r, 0)
            if board[r][cols - 1] == 'O' and (r, cols - 1) not in visit:  # Right edge
                dfs(r, cols - 1)
                #bfs(r, cols - 1)
            
        for c in range(cols): 
            if board[0][c] == 'O' and (0, c) not in visit:  # Top edge
                dfs(0, c)
                #bfs(0, c)
            if board[rows - 1][c] == 'O' and (rows - 1, c) not in visit:  # Bottom edge
                dfs(rows - 1, c)
                #bfs(rows - 1, c)
                    

        for r in range(rows): 
            for c in range(cols): 
                if (r,c) not in visit and board[r][c] == 'O': 
                    board[r][c] = 'X'   
        
```

*   **Time Complexity:** O(rows×cols)

    O(rows×cols)O(rows \times cols)

*   **Space Complexity:** O(rows×cols)

    O(rows×cols)O(rows \times cols)

This complexity is expected for this type of grid traversal problem, and the solution is efficient given the constraints.
