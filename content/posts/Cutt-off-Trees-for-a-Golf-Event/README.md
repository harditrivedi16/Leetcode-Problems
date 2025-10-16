---
id: 1da7e332-de10-808d-9530-ebedc9143a93
title: Cutt off Trees for a Golf Event
created_time: 2025-04-19T16:09:00.000Z
last_edited_time: 2025-10-15T18:13:00.000Z
difficulty_level: Hard
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/cut-off-trees-for-golf-event/description/
my_confidence_level: Low
last_solved: null
concept_involved:
  - Graphs
companies_asked: []
problem_name: Cutt off Trees for a Golf Event

---

```python
from collections import deque

class Solution:
    def cutOffTree(self, forest: List[List[int]]) -> int:
        if not forest or not forest[0]:
            return -1
        
        rows, cols = len(forest), len(forest[0])
        
        # Step 1: Collect and sort trees by height
        trees = []
        for r in range(rows):
            for c in range(cols):
                if forest[r][c] > 1:
                    trees.append((forest[r][c], r, c))
        trees.sort()
        
        # Step 2: BFS function to compute shortest path
        def bfs(sr, sc, tr, tc):
            visited = [[False]*cols for _ in range(rows)]
            queue = deque([(sr, sc, 0)])  # (row, col, steps)
            visited[sr][sc] = True
            while queue:
                r, c, steps = queue.popleft()
                if r == tr and c == tc:
                    return steps
                for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
                    nr, nc = r + dr, c + dc
                    if (0 <= nr < rows and 0 <= nc < cols and 
                        not visited[nr][nc] and forest[nr][nc] != 0):
                        visited[nr][nc] = True
                        queue.append((nr, nc, steps + 1))
            return -1  # unreachable

        # Step 3: Visit trees in order
        total_steps = 0
        sr, sc = 0, 0
        for _, tr, tc in trees:
            steps = bfs(sr, sc, tr, tc)
            if steps == -1:
                return -1
            total_steps += steps
            sr, sc = tr, tc  # Move to next tree
        
        return total_steps

```

### **Approach**

*   **Collect and Sort Trees**:

    *   Traverse the matrix.

    *   Store all cells with value > 1 (trees) and their coordinates.

    *   Sort by tree height.

*   **Shortest Path Between Trees Using BFS**:

    *   For each tree (after sorting), use **BFS from current position** to the next tree’s position.

    *   Keep track of steps taken.

    *   If at any point BFS can’t reach a tree → return `1`.

*   **Update Start Position After Each Tree**:

    *   Once you cut a tree, your new start is its cell.

### Time and Space Complexity

*   **Time Complexity**:

    *   Let `T` be the number of trees.

    *   Each BFS is `O(R × C)` where R = rows, C = cols.

    *   So total time is `O(T × R × C)`.

*   **Space Complexity**:

    *   For BFS queue and visited matrix → `O(R × C)`.
