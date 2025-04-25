---
id: 1db7e332-de10-807e-ae7b-f00f9a885a5a
title: Optimizing Water Distribution in a Village
created_time: 2025-04-20T16:03:00.000Z
last_edited_time: 2025-04-24T16:50:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/optimize-water-distribution-in-a-village/
my_confidence_level: Meduim
number: 96
amazon_prep: 'No'
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Optimizing Water Distribution in a Village

---

### 🔍 **Problem Summary:**

You're given `n` houses. You can either build a well in a house (cost given per house), or connect two houses with a pipe (cost given per pipe). Find the minimum total cost to supply water to all houses.

***

### 🛠️ **Approach:**

We treat the problem as a graph where:

*   Each house is a node.

*   Each pipe is an edge between two nodes.

*   **We add a virtual node (0)** and connect it to every house with the cost of building a well in that house.

*   Then we use **Kruskal's algorithm** to build the MST and compute the minimum total cost.

***

### ✅ **Code:**

```python
python
CopyEdit
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
    def minCostToSupplyWater(self, n: int, wells: List[int], pipes: List[List[int]]) -> int:
        edges = []

        # Add virtual edges from node 0 to each house with well cost
        for i in range(n):
            edges.append([0, i + 1, wells[i]])  # (virtual node, house, cost)

        # Add actual pipe connections
        for u, v, cost in pipes:
            edges.append([u, v, cost])

        # Sort all edges by cost
        edges.sort(key=lambda x: x[2])

        uf = UnionFind(n)
        total_cost = 0

        for u, v, cost in edges:
            if uf.union(u, v):
                total_cost += cost

        return total_cost


```

***

### ⏱️ **Time Complexity:** `O(E log E)`

(`E` is the total number of pipes plus `n` virtual well connections.)

### 📦 **Space Complexity:** `O(N)`

(for the Union-Find data structure)
