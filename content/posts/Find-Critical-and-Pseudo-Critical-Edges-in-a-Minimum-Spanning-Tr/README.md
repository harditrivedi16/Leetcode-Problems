---
id: 1db7e332-de10-80b8-a343-efba32fe2c03
title: Find Critical and Pseudo Critical Edges in a Minimum Spanning Tree
created_time: 2025-04-20T16:03:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/find-cr...
my_confidence_level: Low
number: null
june_interviews_prep: null
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Find Critical and Pseudo Critical Edges in a Minimum Spanning Tree

---

```python
class UnionFind:
    def __init__(self, n):
        # Initialize parent and rank arrays
        self.par = [i for i in range(n)]
        self.rank = [1] * n

    def find(self, x):
        # Find with path compression
        if x != self.par[x]:
            self.par[x] = self.find(self.par[x])
        return self.par[x]

    def union(self, x, y):
        # Union by rank
        px, py = self.find(x), self.find(y)
        if px == py:
            return False  # Cycle detected
        if self.rank[px] < self.rank[py]:
            self.par[px] = py
        else:
            self.par[py] = px
            if self.rank[px] == self.rank[py]:
                self.rank[px] += 1
        return True  # Union successful


class Solution:
    def findCriticalAndPseudoCriticalEdges(self, n: int, edges: List[List[int]]) -> List[List[int]]:
        # Add original index to each edge for result mapping
        indexed_edges = [edge + [i] for i, edge in enumerate(edges)]
        
        # Sort edges by weight for Kruskal's algorithm
        indexed_edges.sort(key=lambda x: x[2])

        # Kruskal's algorithm to get MST cost
        def kruskal(n, edges, skip_edge_index=None, pick_edge=None):
            uf = UnionFind(n)
            cost = 0
            edges_used = 0

            # If we must pick one edge first (for pseudo-critical check)
            if pick_edge:
                u, v, w, _ = pick_edge
                if uf.union(u, v):
                    cost += w
                    edges_used += 1

            for i, (u, v, w, idx) in enumerate(edges):
                if idx == skip_edge_index:
                    continue  # Skip this edge
                if uf.union(u, v):
                    cost += w
                    edges_used += 1
                if edges_used == n - 1:
                    break

            # Only return cost if it's a valid MST
            return cost if edges_used == n - 1 else float('inf')

        # Get original MST cost
        base_cost = kruskal(n, indexed_edges)

        critical, pseudo_critical = [], []

        for u, v, w, i in indexed_edges:
            # Check if edge is critical: removing it increases cost
            if kruskal(n, indexed_edges, skip_edge_index=i) > base_cost:
                critical.append(i)
            # Check if edge is pseudo-critical: including it gives same cost
            elif kruskal(n, indexed_edges, pick_edge=[u, v, w, i]) == base_cost:
                pseudo_critical.append(i)

        return [critical, pseudo_critical]

```

### Quick Recap:

*   **Critical Edge**: If skipping it increases the MST cost → needed for minimum.

*   **Pseudo-Critical Edge**: If forcing it in still gives the same MST cost → not necessary, but can be part of one MST.

**Time Complexity:** `O(E * α(N)) + E^2 * logE` — sorting edges takes `O(E log E)`, and for each edge we run Kruskal’s which is `O(E * α(N))`.

**Space Complexity:** `O(N + E)` — for the Union-Find structure and storing the graph.
