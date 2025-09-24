---
id: 1e27e332-de10-80b6-9643-ffaee3112f66
title: Implement a Trie Prefix tree
created_time: 2025-04-27T19:33:00.000Z
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
problem_name: Implement a Trie Prefix tree

---

# 1) Implement Trie (Prefix Tree)

**Problem Statement:**

Implement a Trie with three operations:

*   `insert(word)`: Insert a word into the trie.

*   `search(word)`: Return true if the word is in the trie.

*   `startsWith(prefix)`: Return true if there is any word in the trie that starts with the given prefix.

```python
python
CopyEdit
class TrieNode:
    def __init__(self):
        self.children = {}  # character -> TrieNode
        self.is_end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word: str) -> None:
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end_of_word = True

    def search(self, word: str) -> bool:
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end_of_word

    def startsWith(self, prefix: str) -> bool:
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True


```

**Intuition:**

We build a tree where each node represents one character.

*   For `insert`, walk through each character and create nodes if they don't exist.

*   For `search`, walk through the characters and check if the path exists and if the end node is marked as the end of a word.

*   For `startsWith`, walk through the prefix and check if the path exists, no need to check if it's the end of a word.

**Time Complexity:**

*   `insert`, `search`, `startsWith`: **O(L)** where L = length of the word or prefix.

**Space Complexity:**

*   In the worst case (many unique strings): **O(N × L)**, where N = number of words, L = average length of a word.
