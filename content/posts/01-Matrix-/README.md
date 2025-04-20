---
id: 1d57e332-de10-8068-8102-c8ddbcb7e6f3
title: '01 Matrix '
created_time: 2025-04-14T20:02:00.000Z
last_edited_time: 2025-04-19T16:05:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/01-matrix/description/
my_confidence_level: Meduim
number: 77
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
  - DFS
  - BFS
companies_asked: []
problem_name: '01 Matrix '

---

```python
class Solution:
    def updateMatrix(self, mat: List[List[int]]) -> List[List[int]]:
        rows, cols = len(mat), len(mat[0])
        dist = [[-1] * cols for _ in range(rows)]
        q = deque()

        for r in range(rows):
            for c in range(cols):
                if mat[r][c] == 0:
                    dist[r][c] = 0
                    q.append((r, c))

        for r, c in q:
            for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
                nr, nc = r + dr, c + dc
                if 0 <= nr < rows and 0 <= nc < cols and dist[nr][nc] == -1:
                    dist[nr][nc] = dist[r][c] + 1
                    q.append((nr, nc))

        return dist

```

*   **Variation:** Multi-source BFS (start from all 0s)

*   **Time:** O(m·n)

*   **Space:** O(m·n)
