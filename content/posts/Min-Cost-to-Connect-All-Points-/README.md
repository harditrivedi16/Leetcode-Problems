---
id: 1db7e332-de10-800f-a776-e7d21fadbcc7
title: 'Min Cost to Connect All Points '
created_time: 2025-04-20T01:59:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://neetcode.io/problems/min-cost...
my_confidence_level: Meduim
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Min Cost to Connect All Points '

---

```python
class Solution:
    def minCostConnectPoints(self, points: List[List[int]]) -> int:
        N = len(points)
        adj = {i: [] for i in range(N)}
        for i in range(N):
            x1, y1 = points[i]
            for j in range(i + 1, N):
                x2, y2 = points[j]
                dist = abs(x1 - x2) + abs(y1 - y2)
                adj[i].append([dist, j])
                adj[j].append([dist, i])

        res = 0
        visit = set()
        minH = [[0, 0]]
        while len(visit) < N:
            cost, i = heapq.heappop(minH)
            if i in visit:
                continue
            res += cost
            visit.add(i)
            for neiCost, nei in adj[i]:
                if nei not in visit:
                    heapq.heappush(minH, [neiCost, nei])
        return res
```

### Problem:

You're given a list of points on a 2D plane. Connect all the points such that the total **cost (Manhattan distance)** of connections is **minimized**, and **each point is connected** (directly or indirectly).

This is equivalent to finding a **Minimum Spanning Tree (MST)** of a fully connected graph where:

*   Nodes = points

*   Edges = pairwise Manhattan distances

***

### 🔹 Approach (Prim's Algorithm):

*   Build an **adjacency list** where each point is connected to all others with edge weights = Manhattan distances.

*   Use a **min-heap (priority queue)** to always select the smallest edge connecting to an unvisited node.

*   Add edges to MST until all nodes are visited.

***

### 🔹 Time Complexity:

*   Building graph (adjacency list): **O(N²)**

*   Heap operations (in worst case): **O(N² \* log N)**

    → because each node can push up to (N - 1) edges.

✅ Overall: **O(N² log N)**

***

### 🔹 Space Complexity:

*   Adjacency list: **O(N²)**

*   Heap and visited set: **O(N)**

    ✅ So total: **O(N²)**
