---
id: 1db7e332-de10-8091-83a5-c6a916cfac21
title: 'Minesweeper '
created_time: 2025-04-20T17:19:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Minesweeper '

---

Too Hard a problem, if asked only give the intuition after giving a thorough thought:

### **Click on Mine**:

*   If the cell you click is a `'M'`, that’s a mine. According to the rules, it immediately turns into `'X'` (you lose).

*   So that's a simple conditional check.

### 2. **Click on Empty Cell (****`'E'`****)**:

We use DFS (or BFS) from this cell:

*   **Step 1: Count Adjacent Mines**

    Look in all 8 directions (up, down, left, right, and diagonals).
    If there's even **1 mine nearby**, update the cell to that number (`'1'` to `'8'`).

*   **Step 2: No Adjacent Mines**

    If there are **no mines nearby**, update the current cell to `'B'` and **recursively reveal all neighbors**, because they’re safe too.

```python
class Solution:
    def updateBoard(self, board: List[List[str]], click: List[int]) -> List[List[str]]:
        rows, cols = len(board), len(board[0])
        directions = [(-1, -1), (-1, 0), (-1, 1),
                      (0, -1),          (0, 1),
                      (1, -1),  (1, 0),  (1, 1)]

        def count_adjacent_mines(r, c):
            count = 0
            for dr, dc in directions:
                nr, nc = r + dr, c + dc
                if 0 <= nr < rows and 0 <= nc < cols and board[nr][nc] == 'M':
                    count += 1
            return count

        def dfs(r, c):
            if board[r][c] != 'E':
                return
            mine_count = count_adjacent_mines(r, c)
            if mine_count > 0:
                board[r][c] = str(mine_count)
            else:
                board[r][c] = 'B'
                for dr, dc in directions:
                    nr, nc = r + dr, c + dc
                    if 0 <= nr < rows and 0 <= nc < cols:
                        dfs(nr, nc)

        r, c = click
        if board[r][c] == 'M':
            board[r][c] = 'X'
        else:
            dfs(r, c)
        return board

```
