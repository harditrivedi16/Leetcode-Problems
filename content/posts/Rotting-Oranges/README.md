---
id: 1da7e332-de10-8014-b4d1-c3e6612bcae0
title: Rotting Oranges
created_time: 2025-04-19T16:05:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/rotting-oranges/description/
my_confidence_level: Meduim
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Rotting Oranges

---

```python
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        rows, cols = len(grid), len(grid[0])
        q = deque()
        fresh = 0

        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 2:
                    q.append((r, c, 0))
                elif grid[r][c] == 1:
                    fresh += 1

        time = 0
        while q:
            r, c, minutes = q.popleft()
            for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
                nr, nc = r + dr, c + dc
                if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == 1:
                    grid[nr][nc] = 2
                    fresh -= 1
                    q.append((nr, nc, minutes + 1))
                    time = minutes + 1

        return time if fresh == 0 else -1

```

*   **Variation:** Time-aware BFS from multiple rotten sources

*   **Time:** O(m·n)

*   **Space:** O(m·n)
