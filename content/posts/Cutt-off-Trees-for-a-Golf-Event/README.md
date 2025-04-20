---
id: 1da7e332-de10-808d-9530-ebedc9143a93
title: Cutt off Trees for a Golf Event
created_time: 2025-04-19T16:09:00.000Z
last_edited_time: 2025-04-19T19:29:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/cut-off-trees-for-golf-event/description/
my_confidence_level: Low
number: 80
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Cutt off Trees for a Golf Event

---

```python
class Solution:
    def cutOffTree(self, forest: List[List[int]]) -> int:
        rows, cols = len(forest), len(forest[0])
        trees = sorted((h, r, c) for r in range(rows) for c in range(cols) if forest[r][c] > 1)

        def bfs(sr, sc, tr, tc):
            if sr == tr and sc == tc:
                return 0
            visited = set()
            q = deque([(sr, sc, 0)])
            visited.add((sr, sc))
            while q:
                r, c, d = q.popleft()
                for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
                    nr, nc = r + dr, c + dc
                    if 0 <= nr < rows and 0 <= nc < cols and (nr, nc) not in visited and forest[nr][nc] != 0:
                        if (nr, nc) == (tr, tc):
                            return d + 1
                        visited.add((nr, nc))
                        q.append((nr, nc, d + 1))
            return -1

        sr = sc = total_steps = 0
        for _, tr, tc in trees:
            steps = bfs(sr, sc, tr, tc)
            if steps == -1:
                return -1
            total_steps += steps
            sr, sc = tr, tc
        return total_steps

```

*   **Variation:** Repeated BFS to each tree in increasing height order

*   **Time:** O(T · m · n), where T is number of trees

*   **Space:** O(m·n) per BFS call
