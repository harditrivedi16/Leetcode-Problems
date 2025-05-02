---
id: 1df7e332-de10-809e-a894-cccf74a4806c
title: Design Tic-Tac -Toe
created_time: 2025-04-24T16:55:00.000Z
last_edited_time: 2025-05-01T15:22:00.000Z
difficulty_level: 'Meduim '
remarks: No need to make the whole board just keep track of count
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/design-tic-tac-toe/?envType=problem-list-v2&envId=7p5x763
my_confidence_level: High
number: 67
amazon_prep: 'Yes'
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked: []
problem_name: Design Tic-Tac -Toe

---

```python
class TicTacToe:

    def __init__(self, n: int):
        # Size of the board
        self.n = n
        
        # Track row and column counts
        self.rows = [0] * n
        self.cols = [0] * n
        
        # Track diagonals
        self.diag = 0
        self.anti_diag = 0

    def move(self, row: int, col: int, player: int) -> int:
        # Player 1 → +1, Player 2 → -1
        add = 1 if player == 1 else -1
        
        # Update row and column counts
        self.rows[row] += add
        self.cols[col] += add
        
        # If it's a diagonal move (top-left to bottom-right)
        if row == col:
            self.diag += add
        
        # If it's anti-diagonal (top-right to bottom-left)
        if row + col == self.n - 1:
            self.anti_diag += add
        
        # Check if any count reaches n (win condition)
        if (abs(self.rows[row]) == self.n or
            abs(self.cols[col]) == self.n or
            abs(self.diag) == self.n or
            abs(self.anti_diag) == self.n):
            return player
        
        # No one wins yet
        return 0


```

## Intuition

Instead of checking the entire board after every move (which is slow), we can be smart:

*   A player **wins** if:

    *   Any **row** has all same symbols

    *   Any **column** has all same symbols

    *   One of the **two diagonals** has all same symbols

So we **don’t need the full board**. We just need **counts**.

For each player:

*   Track how many moves they’ve made in each row, column, and diagonals

*   If any count reaches `n`, that player wins

This allows us to make each move in constant time!

***

## 🔹 Data Structures Used & Why

We use:

*   Two arrays: `rows[n]` and `cols[n]`

*   Two integers: `diag` and `anti_diag`

Instead of tracking each player separately, we can **add +1 for player 1, -1 for player 2**

If any of the counts hits `+n` → player 1 wins

If any of the counts hits `-n` → player 2 wins

> ✅ This trick helps us avoid maintaining separate counters per player

## Time and Space Complexity

Let’s break it down in simple language:

### ⏱ Time Complexity: **O(1)** per move

*   We’re not looping over the whole board.

*   Every move updates 4 counters: `row`, `col`, `diag`, `anti_diag`

*   All done in **constant time**

> ⚡ Very efficient — even if the board is large, each move takes the same time.

***

### 💾 Space Complexity: **O(n)**

*   We store:

    *   One array of size `n` for rows

    *   One array of size `n` for columns

    *   Two variables for diagonals

So overall:

*   Space = `2n + 2` → **O(n)**
