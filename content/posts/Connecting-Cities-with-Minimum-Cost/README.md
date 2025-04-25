---
id: 1db7e332-de10-8048-9d54-efc923880356
title: Connecting Cities with Minimum Cost
created_time: 2025-04-20T01:59:00.000Z
last_edited_time: 2025-04-24T16:50:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/connecting-cities-with-minimum-cost/
my_confidence_level: Meduim
number: 95
amazon_prep: 'No'
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Connecting Cities with Minimum Cost

---

```python
class UnionFind:
    def __init__(self, n):
        self.par = [i for i in range(n + 1)]
        self.rank = [1] * (n + 1)

    def find(self, x):
        while x != self.par[x]:
            self.par[x] = self.par[self.par[x]]  # Path compression
            x = self.par[x]
        return x

    def union(self, x, y):
        p1, p2 = self.find(x), self.find(y)
        if p1 == p2:
            return False
        if self.rank[p1] < self.rank[p2]:
            self.par[p1] = p2
            self.rank[p2] += self.rank[p1]
        else:
            self.par[p2] = p1
            self.rank[p1] += self.rank[p2]
        return True

class Solution:
    def minimumCost(self, n: int, connections: List[List[int]]) -> int:
        # Sort all connections based on cost
        connections.sort(key=lambda x: x[2])
        
        uf = UnionFind(n)
        total_cost = 0
        edges_used = 0
        
        for u, v, cost in connections:
            if uf.union(u, v):
                total_cost += cost
                edges_used += 1
                if edges_used == n - 1:
                    return total_cost
        
        return -1  # Return -1 if not all cities can be connected

```

### 🔍 **Approach:**

Use **Kruskal’s Algorithm** to build a Minimum Spanning Tree (MST) from the list of connections between cities. We sort the edges by cost and use Union-Find to add edges that don't form a cycle.

### ⏱️ **Time Complexity:** `O(E log E)`

(Sorting edges takes `E log E`, where `E` is the number of connections.)

### 📦 **Space Complexity:** `O(N)`

(for parent and rank arrays in Union-Find)
