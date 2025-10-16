---
id: 1db7e332-de10-8032-b701-e309ddb23d1e
title: 'Alien Dictionary '
created_time: 2025-04-20T17:17:00.000Z
last_edited_time: 2025-10-15T18:14:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
last_solved: null
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Alien Dictionary '

---

You're given a list of words **sorted lexicographically** *by an alien language*.

Your job:

> Deduce the order of characters in that alien language and return it as a string.

### Step-by-Step Breakdown:

*   **Build a graph** of characters:

    *   For each pair of words, find the **first character where they differ**.

    *   That tells you:

        👉 `char1 < char2` → put an edge from `char1 → char2`.

*   **Topological sort** this graph:

    *   It gives a valid **linear ordering** of characters respecting the edges.

*   **Return the ordering as a string**.

***

### ⚠️ Edge Case:

If one word is a prefix of another, like:

```python
python
CopyEdit
["abc", "ab"]


```

This is **invalid** because "abc" shouldn't come before "ab". Return `""` in such cases.

***

### ✅ Code (Clean & Commented):

```python
python
CopyEdit
from collections import defaultdict, deque

def alienOrder(words):
    # Step 1: Build the graph
    adj = defaultdict(set)
    indegree = {char: 0 for word in words for char in word}

    for i in range(len(words) - 1):
        w1, w2 = words[i], words[i + 1]
        min_len = min(len(w1), len(w2))

        # Check for invalid case like ["abc", "ab"]
        if w1[:min_len] == w2[:min_len] and len(w1) > len(w2):
            return ""

        for j in range(min_len):
            if w1[j] != w2[j]:
                if w2[j] not in adj[w1[j]]:
                    adj[w1[j]].add(w2[j])
                    indegree[w2[j]] += 1
                break

    # Step 2: Topological Sort using Kahn's Algorithm
    q = deque([char for char in indegree if indegree[char] == 0])
    res = []

    while q:
        char = q.popleft()
        res.append(char)
        for nei in adj[char]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                q.append(nei)

    if len(res) < len(indegree):
        return ""  # Cycle detected

    return "".join(res)


```

***

### 🧠 Time & Space Complexity

*   **Time:** `O(C)` where `C` is total number of characters across all words.

*   **Space:** `O(U + E)` — U = unique characters, E = edges between characters.
