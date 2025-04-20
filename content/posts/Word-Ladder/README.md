---
id: 1da7e332-de10-805d-a1fd-d77b395509a4
title: Word Ladder
created_time: 2025-04-19T17:14:00.000Z
last_edited_time: 2025-04-19T19:30:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/word-ladder/description/
my_confidence_level: Low
number: 81
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Word Ladder

---

```python
class Solution:
    def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
        if endWord not in wordList:
            return 0

        nei = collections.defaultdict(list)
        wordList.append(beginWord)
        for word in wordList:
            for j in range(len(word)):
                pattern = word[:j] + "*" + word[j + 1 :]
                nei[pattern].append(word)

        visit = set([beginWord])
        q = deque([beginWord])
        res = 1
        while q:
            for i in range(len(q)):
                word = q.popleft()
                if word == endWord:
                    return res
                for j in range(len(word)):
                    pattern = word[:j] + "*" + word[j + 1 :]
                    for neiWord in nei[pattern]:
                        if neiWord not in visit:
                            visit.add(neiWord)
                            q.append(neiWord)
            res += 1
        return 0
```

Time Complexity: O(m^2\* n)
Space COmplexit: O(m^2\* n)

# **Time & Space Complexity Explanation**

Let’s break down why this `Word Ladder` BFS solution has a time complexity of **O(m² \* n)**, where:

*   `n` = number of words in `wordList`

*   `m` = length of each word (all words are the same length)

***

### 💡 **Key Operations in the Code:**

*   **Building the adjacency list (****`nei`****)**:

    *   For each word (`n` words), generate `m` patterns by replacing one character at a time → `O(m * n)`.

*   **BFS Traversal**:

    *   In the worst case, we may explore every word (`n`) from every pattern (`m` patterns per word).

    *   For each word popped from the queue, we generate `m` patterns, and for each pattern we access the list of neighbor words.

    *   Each pattern lookup is `O(1)`, but the number of neighbor words in each list could be up to `n`, so:

        *   For each of the `n` words, in the worst case, we process `m` patterns and up to `n` neighbors:

            → **O(m \* n)** neighbors total per word.

So the **total** worst-case time complexity across all BFS levels is:

```plain text
mathematica
CopyEdit
O(n) words × O(m) patterns per word × O(n) neighbors per pattern
= O(m * n * n) = O(m * n²)


```

But we **only visit each word once**, and each word has `m` patterns, so we don’t reprocess. That’s why we often simplify the upper bound to:

***

### ✅ **Final Time Complexity:** **`O(m² * n)`**

Why `m²`?

*   Because pattern creation and comparison is **O(m)**, and we do that inside a loop that already runs `O(m)` times per word.

SPace COmplexity Explaination

### Why it's `O(m² * n)`:

*   **Neighbor map** **`nei`\*\*\*\*:**

    *   For each word (`n` total), you create `m` patterns (like `h*t`, `it`, etc.)

    *   Each pattern is a string of length `m` → storing `m`length strings as keys, and storing up to `n` words as values for each pattern

    *   So, total space to store keys and values = `O(m² * n)`

*   **Visited Set** **`visit`\*\*\*\*:**

    *   Can hold up to `n` words → `O(n)`

*   **Queue** **`q`\*\*\*\*:**

    *   BFS queue can hold up to `n` words → `O(n)`
