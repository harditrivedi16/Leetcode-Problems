---
id: 1da7e332-de10-80a3-ab85-d3836474efb9
title: 'Word Ladder II '
created_time: 2025-04-19T17:20:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: Hard
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/word-ladder-ii/description/
my_confidence_level: Low
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Word Ladder II '

---

### **Problem Variation from Word Ladder I**

*   **Word Ladder I** asks for the **shortest path length** from `beginWord` to `endWord`.

*   **Word Ladder II** asks for **all the shortest transformation sequences** from `beginWord` to `endWord`.

***

### 🔹 **Key Differences in Logic & Code**

*   **Track all paths**, not just shortest length.

*   Use **BFS to build the graph of shortest paths**, then **DFS to backtrack** and collect all valid sequences.

*   Use a **`parents`** **map** to store how each word was reached (from which words), to reconstruct all paths.

***

### 🔹 **Code: Word Ladder II**

```python
python
CopyEdit
from collections import defaultdict, deque
class Solution:
    def findLadders(self, beginWord: str, endWord: str, wordList: List[str]) -> List[List[str]]:
        wordSet = set(wordList)
        if endWord not in wordSet:
            return []

        # Step 1: BFS to build graph and parents map
        parents = defaultdict(set)
        level = {beginWord}
        found = False

        while level and not found:
            next_level = defaultdict(set)
            for word in level:
                for i in range(len(word)):
                    for c in 'abcdefghijklmnopqrstuvwxyz':
                        new_word = word[:i] + c + word[i+1:]
                        if new_word in wordSet and new_word != word:
                            next_level[new_word].add(word)
                            if new_word == endWord:
                                found = True
            wordSet -= set(next_level.keys())  # Remove visited
            level = next_level
            for word in next_level:
                parents[word] |= next_level[word]

        # Step 2: DFS to collect all paths
        res = []

        def dfs(word, path):
            if word == beginWord:
                res.append([beginWord] + path[::-1])
                return
            for p in parents[word]:
                dfs(p, path + [word])

        if found:
            dfs(endWord, [])

        return res


```

***

### 🔹 **Time Complexity:** **`O(n * m²)`** **to** **`O(n² * m)`**

*   `n = number of words`, `m = length of each word`

*   BFS explores all `n` words with `m` positions and 26 characters: `O(n * m * 26)`

*   DFS builds all shortest paths. In worst case, exponential paths could be returned, but we only build minimal-length ones.

> So practical time: O(n \* m²) to O(n² \* m) depending on graph width.

***

### 🔹 **Space Complexity:** **`O(n * m)`**

*   Parents map stores edges: up to `n` words, each with several parents.

*   Level set, DFS recursion stack, and results list can also take space up to `O(n * m)`.
