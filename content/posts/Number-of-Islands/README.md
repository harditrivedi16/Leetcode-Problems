---
id: 1767e332-de10-809c-909b-e8583fab48d2
title: Number of Islands
created_time: 2025-01-09T01:15:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Amazon Questions
  - Top Interview Questions
  - Top Microsoft Questions
problem_link: https://leetcode.com/problems/number-of-islands/submissions/1510895518/
my_confidence_level: Low
last_solved: 2025-03-24T00:00:00.000Z
concept_involved:
  - DFS
  - Graphs
  - BFS
companies_asked:
  - Amazon
  - Google
  - Bloomberg
  - Microsoft
  - Facebook/Meta
  - Uber
  - Apple
  - TicTok
problem_name: Number of Islands

---

### DFS Approach

```python
def numIslands(grid):
    if not grid:
        return 0
    
    rows, cols = len(grid), len(grid[0])
    visited = [[False for _ in range(cols)] for _ in range(rows)]
    
    def dfs(r, c):
        # Base case: if out of bounds, visited, or water
        if r < 0 or c < 0 or r >= rows or c >= cols or visited[r][c] or grid[r][c] == '0':
            return
        
        # Mark current cell as visited
        visited[r][c] = True
        
        # Visit all 4 possible directions (up, down, left, right)
        dfs(r - 1, c)  # Up
        dfs(r + 1, c)  # Down
        dfs(r, c - 1)  # Left
        dfs(r, c + 1)  # Right
    
    islands = 0
    for r in range(rows):
        for c in range(cols):
            # If we find unvisited land, it's a new island
            if grid[r][c] == '1' and not visited[r][c]:
                islands += 1
                dfs(r, c)  # Perform DFS to mark the entire island
    
    return islands

```

### BFS Approach:

```python
class Solution: 
	def noOfIslands():
		if not grid: 
        return 0
        
        rows, cols = len(grid), len(grid[0])
        visited = set()
        islands = 0 

        def bfs(r,c): 
            q = deque()
            q.append((r,c))
            visited.add((r,c))

            while q: 
                row, col = q.popleft()
                directions = [[1,0], [-1,0], [0,1], [0,-1]]

                for dr,dc in directions: 
                    r = row + dr
                    c = col + dc

                    if (r in range(rows) and 
                       c in range(cols) and 
                       grid[r][c] == '1' and 
                       (r,c) not in visited): 

                       q.append((r,c))
                       visited.add((r,c))

        for r in range(rows):
            for c in range(cols): 
                if grid[r][c] == '1' and (r,c) not in visited: 
                    bfs(r,c)
                    islands+= 1
        return islands


    
```

### **Time Complexity**

Both **BFS** and **DFS**: **O(M × N)**, where **M** and **N** are grid dimensions.

Each cell is visited once, making work proportional to grid size.

***

### **Space Complexity**

**DFS**: **O(M × N)** worst case due to recursion stack depth.

**BFS**: **O(min(M, N))** average, **O(M × N)** worst case due to queue size.
