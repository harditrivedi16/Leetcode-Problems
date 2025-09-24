---
id: 1e27e332-de10-802b-82c8-ca06e6c0b886
title: Design Add & Search Word Data Structure
created_time: 2025-04-27T19:45:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Trie
companies_asked: []
problem_name: Design Add & Search Word Data Structure

---

# Design Add and Search Word Data Structure

**Problem Statement:**

You need to design a data structure that supports two operations:

*   `addWord(word)`: Add a word into the data structure.

*   `search(word)`: Search for a word in the data structure.

    **Important twist:**

    *   The word can contain the dot character `'.'`, which can represent **any letter** (wildcard matching).

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end_of_word = False

class WordDictionary:
    def __init__(self):
        self.root = TrieNode()
        
    def addWord(self, word: str) -> None:
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end_of_word = True
        
    def search(self, word: str) -> bool:
        def dfs(j, node):
            for i in range(j, len(word)):
                char = word[i]
                if char == '.':
                    # Explore all children
                    for child in node.children.values():
                        if dfs(i + 1, child):
                            return True
                    return False
                else:
                    if char not in node.children:
                        return False
                    node = node.children[char]
            return node.is_end_of_word
        
        return dfs(0, self.root)

```

**Intuition:**

This is **almost the same** as a regular Trie, but because of the wildcard `'.'`, the `search()` needs to be able to **branch out** and **explore all possibilities** at that character.

That means:

*   For normal letters, follow the path.

*   For `'.'`, recursively search *all* children at that level.

**Time Complexity:**

*   `addWord`: **O(L)** where L = length of the word.

*   `search`:

    *   Worst case **O(26^L)** (if many `'.'` are used and full branching happens).

    *   Average case is much faster if few wildcards.

**Space Complexity:**

*   Same as Trie: **O(N × L)** where N = number of words, L = average length.

Is dfs function inside , is a good coding practice:

*   For *small DFS, BFS, or helper logic tightly tied to one function*, nesting functions is totally fine (even encouraged for clarity).

*   For *larger DFS or reusable logic*, yes, we pull it out and make it a separate method.
