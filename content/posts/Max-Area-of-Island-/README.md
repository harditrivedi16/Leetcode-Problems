---
id: 1767e332-de10-805b-971e-d265a252a9b4
title: 'Max Area of Island '
created_time: 2025-01-09T01:16:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/max-area-of-island/submissions/1511013650/
my_confidence_level: Meduim
number: 52
last_solved: 2025-01-16T00:00:00.000Z
concept_involved:
  - BFS
  - DFS
  - Graphs
companies_asked:
  - Facebook/Meta
  - Google
  - Microsoft
  - DoorDash
  - TicTok
  - GrubHub
problem_name: 'Max Area of Island '

---

```python
from collections import deque

class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        if not grid: 
            return 0 
        
        rows, cols = len(grid), len(grid[0])
        visit = set()
        
        maxArea = 0 

        def dfs(r,c)-> int: 

            if r <0 or r >= rows or c < 0 or c >= cols or grid[r][c] != 1 or (r,c) in visit: 
                return 0
            
            area = 1
            visit.add((r,c))

            area += dfs(r + 1, c)
            area += dfs(r - 1, c)
            area += dfs(r, c + 1)
            area += dfs(r, c - 1)
            return area

        def bfs(r,c): 
            q = deque()
            q.append((r,c))
            visit.add((r,c))
            area = 1

            while q: 
                row, col = q.popleft()
                directions = [[1,0], [-1,0], [0,1], [0,-1]]

                for dr, dc in directions: 
                    r = row + dr
                    c = col + dc
                    if r in range(rows) and c in range(cols) and grid[r][c] == 1 and (r,c) not in visit: 
                        area += 1
                        visit.add((r,c))
                        q.append((r,c))
            return area 

        for r in range(rows): 
            for c in range(cols): 
                if grid[r][c] == 1 and (r,c) not in visit:
                    area = bfs(r,c)
                    #area = dfs(r,c)
                    maxArea = max(area, maxArea)
        return maxArea



        
```

Time Complexity = O(mxn)

Space Complexity= O(mxn)
