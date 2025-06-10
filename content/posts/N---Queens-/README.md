---
id: 1e47e332-de10-80bc-96d3-f98b5aa4a120
title: 'N - Queens '
created_time: 2025-04-29T18:56:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
june_interviews_prep: null
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - BackTracking
companies_asked: []
problem_name: 'N - Queens '

---

**Problem Statement:**

The **N-Queens** puzzle is the problem of placing N chess queens on an **N×N** chessboard such that no two queens threaten each other.

Given an integer `n`, return all distinct solutions to the **N-Queens** puzzle. You may return the answer in any order.

A solution involves placing queens such that no two queens share the same row, column, or diagonal.

**Example:**

Input: `n = 4`

Output:

```plain text
cpp
CopyEdit
[
  [".Q..",  // Solution 1
   "...Q",
   "Q...",
   "..Q."],

  ["..Q.",  // Solution 2
   "Q...",
   "...Q",
   ".Q.."]
]


```

```python
def solveNQueens(n):
    def is_valid(board, row, col):
        for i in range(row):
            if board[i] == col or \
               board[i] - i == col - row or \
               board[i] + i == col + row:
                return False
        return True

    def backtrack(row, board):
        if row == n:
            result.append(["." * i + "Q" + "." * (n - i - 1) for i in board])
            return
        
        for col in range(n):
            if is_valid(board, row, col):
                board.append(col)
                backtrack(row + 1, board)
                board.pop()
    
    result = []
    backtrack(0, [])
    return result

```

The **N-Queens problem** is about placing `N` queens on an `N x N` chessboard such that no two queens threaten each other. A queen can attack another if they're in the same row, column, or diagonal.

### Approach: **Backtracking**

*   **Start with the first row** and attempt to place a queen in each column.

*   **Validate placement**: Before placing a queen, check that it doesn’t conflict with previously placed queens:

    *   Same column

    *   Same positive diagonal (`row - col`)

    *   Same negative diagonal (`row + col`)

*   **Move to the next row** and repeat the process of placing queens, validating each placement.

*   **Backtrack if stuck**: If no valid positions exist in the current row, backtrack to the previous row and move the queen to the next valid column.

*   **Record solutions**: If all rows are filled successfully, record the board configuration as a solution.

### Key Concept: **Backtracking**

Backtracking allows us to explore all possible configurations while pruning invalid solutions early, making it more efficient than brute-forcing through all combinations. If we hit a conflict, we can "backtrack" by removing the last placed queen and trying a new position for it.

This is an example of **depth-first search** (DFS) with pruning.

### Time Complexity:

*   For each row, we try placing a queen in each of the `n` columns.

*   So, for an `n x n` board, there are `n!` possible configurations in the worst case.

*   Thus, the time complexity is **O(n!)** due to the factorial number of possible placements.

### Space Complexity:

*   We store the current state of the board as a list of column indices.

*   The recursion depth can go up to `n`, and for each solution, we store `n` positions.

*   Therefore, the space complexity is **O(n)** for storing the current board and **O(n!)** for storing all solutions.
