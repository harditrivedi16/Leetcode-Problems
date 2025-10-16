---
id: 17e7e332-de10-803b-8dbc-d682c62ed03a
title: Word Search
created_time: 2025-01-17T02:42:00.000Z
last_edited_time: 2025-10-15T18:10:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/word-search/
my_confidence_level: Low
last_solved: null
concept_involved:
  - DFS
  - BackTracking
  - Graphs
companies_asked:
  - Amazon
  - Bloomberg
  - Google
  - TicTok
  - Microsoft
  - Uber
  - Facebook/Meta
problem_name: Word Search

---

```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        if not board or not word: 
            return False 
        
        ROWS, COLS = len(board), len(board[0])
        visit = set()

        def dfs(r, c, word_idx): 

            if word_idx == len(word): 
                return True
            
            if (r < 0 or r >= ROWS or c < 0 or c >= COLS or word[word_idx] != board[r][c] or (r,c) in visit): 
                return False
            
            visit.add((r,c))

            result = (dfs(r + 1, c, word_idx + 1) or
                      dfs(r - 1, c, word_idx + 1) or
                      dfs(r, c + 1, word_idx + 1) or
                      dfs(r, c - 1, word_idx + 1)   )
            visit.remove((r,c))
            return result
        
        for r in range(ROWS): 
            for c in range(COLS): 
                if dfs(r, c, 0): 
                    return True
        return False


```

Time Complexity: O(n \*m \* 4^len(word))

Space Complexity: O(m\*n)
