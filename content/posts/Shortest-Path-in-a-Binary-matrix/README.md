---
id: 1da7e332-de10-80fd-8153-d4f8dccfc425
title: Shortest Path in a Binary matrix
created_time: 2025-04-19T16:06:00.000Z
last_edited_time: 2025-04-19T19:29:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/shortest-path-in-binary-matrix/description/
my_confidence_level: Low
number: 79
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Shortest Path in a Binary matrix

---

```python
class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        rows, cols = len(grid), len(grid[0])
        if grid[0][0] != 0 or grid[rows-1][cols-1] != 0:
            return -1

        q = deque([(0, 0, 1)])
        visited = set((0, 0))

        directions = [(1,0), (-1,0), (0,1), (0,-1), (1,1), (-1,-1), (1,-1), (-1,1)]

        while q:
            r, c, dist = q.popleft()
            if r == rows-1 and c == cols-1:
                return dist
            for dr, dc in directions:
                nr, nc = r + dr, c + dc
                if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == 0 and (nr, nc) not in visited:
                    visited.add((nr, nc))
                    q.append((nr, nc, dist + 1))
        return -1

```

*   **Variation:** 8-direction BFS, shortest path to bottom-right

*   **Time:** O(m·n)

*   **Space:** O(m·n)
