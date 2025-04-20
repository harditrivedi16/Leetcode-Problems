---
id: 1da7e332-de10-8079-a75f-e48ee4d02b9d
title: Graph valid Tree
created_time: 2025-04-19T17:23:00.000Z
last_edited_time: 2025-04-19T19:30:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/graph-valid-tree/description/
my_confidence_level: Low
number: 83
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Graph valid Tree

---

```python
class Solution:
    def validTree(self, n: int, edges: List[List[int]]) -> bool:
        if len(edges) > (n - 1):
            return False
        
        adj = [[] for _ in range(n)]
        for u, v in edges:
            adj[u].append(v)
            adj[v].append(u)
        
        visit = set()
        def dfs(node, par):
            if node in visit:
                return False
            
            visit.add(node)
            for nei in adj[node]:
                if nei == par:
                    continue
                if not dfs(nei, node):
                    return False
            return True
        
        return dfs(0, -1) and len(visit) == n
```

This code has a **time and space complexity of O(V + E)** because:

*   It constructs an adjacency list from the edge list, which takes **O(E)** time and space.

*   It then performs a **DFS traversal**, visiting each node and edge once, resulting in **O(V + E)** time.

*   The `visit` set and adjacency list both use **O(V + E)** space to store nodes and edges.
