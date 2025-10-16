---
id: 1317e332-de10-814d-a1a3-f9d15bd18530
title: 'Valid Sudoku '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top Interview Questions
problem_link: https://leetcode.com/problems/valid-sudoku/description/
my_confidence_level: High
last_solved: null
concept_involved:
  - Arrays
  - Sets
companies_asked:
  - Amazon
  - Microsoft
  - Apple
  - Bloomberg
  - Uber
  - Linkedin
  - Snap
problem_name: 'Valid Sudoku '

---

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:

        cols = collections.defaultdict(set)
        rows = collections.defaultdict(set)
        squares = collections.defaultdict(set) # key [(r//3, c//3)]


        for r in range(9):
            for c in range(9): 
                if board[r][c] == '.': 
                    continue 
                if (board[r][c] in rows[r] or 
                   board[r][c] in cols[c] or 
                   board[r][c] in squares[(r//3,c//3)]): 
                   return False 
                cols[c].add(board[r][c])
                rows[r].add(board[r][c])
                squares[(r//3,c//3)].add(board[r][c])

        return True 


        
```

This solution checks if a given Sudoku board is valid by ensuring that no number appears more than once in any row, column, or 3x3 subgrid.

```python

if (board[r][c] in rows[r] or board[r][c] in cols[c] or board[r][c] in squares[(r//3,c//3)]):
    # If the current number already exists in the row, column, or 3x3 grid, the Sudoku is invalid
    return False


```

This line explains that if the current number is already present in the corresponding row, column, or 3x3 grid, it breaks the Sudoku rule of uniqueness, so we return `False`. This is the key condition that validates the board.

**Time Complexity**: O(1), since the board size is fixed at 9x9, making the number of operations constant.
**Space Complexity**: O(1), as the space used for rows, columns, and squares is bounded by the fixed size of the board.

Any edge cases that this approach saves?
Since you've handled empty cells (represented by `.`) by skipping them, you're correctly allowing for incomplete boards without running into errors.
