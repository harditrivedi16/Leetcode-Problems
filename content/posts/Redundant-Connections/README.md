---
id: 1db7e332-de10-80ee-ab8a-cad88072910d
title: Redundant Connections
created_time: 2025-04-20T01:59:00.000Z
last_edited_time: 2025-04-24T16:50:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/redunda...
my_confidence_level: Meduim
number: 93
amazon_prep: 'No'
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Redundant Connections

---

```python
class Solution:
    def findRedundantConnection(self, edges: List[List[int]]) -> List[int]:
        par = [i for i in range(len(edges) + 1)]
        rank = [1] * (len(edges) + 1)

        def find(n):
            p = par[n]
            while p != par[p]:
                par[p] = par[par[p]]
                p = par[p]
            return p

        def union(n1, n2):
            p1, p2 = find(n1), find(n2)

            if p1 == p2:
                return False
            if rank[p1] > rank[p2]:
                par[p2] = p1
                rank[p1] += rank[p2]
            else:
                par[p1] = p2
                rank[p2] += rank[p1]
            return True

        for n1, n2 in edges:
            if not union(n1, n2):
                return [n1, n2]
```

### Problem Statement:

You're given a **tree** with `n` nodes (1-indexed), and **one extra edge** is added, forming a cycle. Return the redundant edge that, if removed, will make the graph a tree again.

***

### 🔹 Why `number of nodes = len(edges)`?

In a tree with `n` nodes, there are always `n - 1` edges. Since one **extra edge** is added, total edges = `n`.

So, `n = len(edges)`, and we initialize the `par` and `rank` arrays accordingly.

***

### 🔹 Union-Find Intuition:

We try to **connect all edges** using union-find:

*   If two nodes are already connected (i.e., they share the same root), adding this edge would create a **cycle**.

*   That edge is the **redundant connection**, and we return it.

***

### 🔹 Time and Space Complexity:

*   **Time:** `O(n * α(n)) ≈ O(n)` where `α(n)` is the inverse Ackermann function (very slow-growing)

*   **Space:** `O(n)` for `par` and `rank` arrays

Let me know if you want to visualize this or walk through a sample input.
