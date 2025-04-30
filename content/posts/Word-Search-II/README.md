---
id: 1e27e332-de10-80b9-9eaf-d8a72b77a8d7
title: Word Search II
created_time: 2025-04-27T20:07:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
amazon_prep: 'Yes'
last_solved: null
concept_involved:
  - Trie
  - BackTracking
  - DFS
companies_asked: []
problem_name: Word Search II

---

### Problem Statement (Word Search II)

You are given a 2D board of letters and a list of words.

Find all the words from the list that can be constructed from letters of sequentially adjacent cells (horizontally or vertically).

*   You can’t reuse the same letter cell twice.

***

###

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.word = None  # Store complete word at the end node

class Solution:
    def findWords(self, board: List[List[str]], words: List[str]) -> List[str]:
        root = TrieNode()

        # Build the Trie
        for w in words:
            node = root
            for c in w:
                if c not in node.children:
                    node.children[c] = TrieNode()
                node = node.children[c]
            node.word = w  # Mark the end of a word

        rows, cols = len(board), len(board[0])
        res = []

        def dfs(r, c, node):
            char = board[r][c]
            if char not in node.children:
                return
            next_node = node.children[char]

            if next_node.word:
                res.append(next_node.word)
                next_node.word = None  # Avoid duplicate adding

            board[r][c] = "#"  # Mark visited

            for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
                nr, nc = r + dr, c + dc
                if 0 <= nr < rows and 0 <= nc < cols and board[nr][nc] != "#":
                    dfs(nr, nc, next_node)

            board[r][c] = char  # Backtrack

        # Start DFS from every cell
        for r in range(rows):
            for c in range(cols):
                dfs(r, c, root)

        return res

```

### Time Complexity

*   Building Trie: `O(L)` where `L = sum(length of all words)`

*   DFS:

    *   Worst case, we visit each cell multiple times: `O(N * M * 4^L)`

*   However, Trie **prunes** early, making real complexity much better than naive DFS.

***

### 📦 Space Complexity

*   Trie space: `O(L)` where `L = sum(length of all words)`

*   Recursion stack: up to `O(L)` depth

*   Result list space: depends on how many words we find.
