---
id: 1db7e332-de10-802a-ba5e-f4edc073549b
title: Shortest Bridge
created_time: 2025-04-20T17:20:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Graphs
companies_asked: []
problem_name: Shortest Bridge

---

You're given a 2D binary grid where `1` represents land and `0` represents water. There are exactly two islands. You must flip `0`s to `1`s to connect the two islands, and return the minimum number of `0`s that need to be flipped to connect them.

```python
from collections import deque

class Solution:
    def shortestBridge(self, grid: List[List[int]]) -> int:
        rows, cols = len(grid), len(grid[0])
        visit = set()
        q = deque()

        def dfs(r, c):
            if (r < 0 or r >= rows or 
                c < 0 or c >= cols or 
                (r, c) in visit or grid[r][c] == 0):
                return
            visit.add((r, c))
            q.append((r, c))
            dfs(r + 1, c)
            dfs(r - 1, c)
            dfs(r, c + 1)
            dfs(r, c - 1)

        # Step 1: Find first island and mark all its land
        found = False
        for r in range(rows):
            if found: break
            for c in range(cols):
                if grid[r][c] == 1:
                    dfs(r, c)
                    found = True
                    break

        # Step 2: BFS from first island to reach the second
        steps = 0
        directions = [(1,0), (-1,0), (0,1), (0,-1)]

        while q:
            for _ in range(len(q)):
                r, c = q.popleft()
                for dr, dc in directions:
                    nr, nc = r + dr, c + dc
                    if 0 <= nr < rows and 0 <= nc < cols and (nr, nc) not in visit:
                        if grid[nr][nc] == 1:
                            return steps
                        visit.add((nr, nc))
                        q.append((nr, nc))
            steps += 1


```

### **Intuition**

You are given a binary grid with exactly two islands (groups of `1`s). The goal is to connect them by flipping as few `0`s to `1`s as possible.

**Steps**:

*   **Use DFS** to find and mark all cells of the first island and store their coordinates in a queue.

*   **Use BFS** from all the border cells of the first island simultaneously to reach the second island.

*   The first time you hit a `1` from the second island during BFS, return the current level — that’s the shortest bridge.

### ⏱ **Time Complexity**

*   **DFS** to mark the first island: `O(N^2)`

*   **BFS** in worst case (entire grid): `O(N^2)`

*   **Overall**: `O(N^2)` where `N` is the number of rows or columns (since grid is `N x N`)

### 💾 **Space Complexity**

*   Visited set and queue: up to `O(N^2)`

*   **Overall**: `O(N^2)`
