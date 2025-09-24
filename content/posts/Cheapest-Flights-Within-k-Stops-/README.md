---
id: 1db7e332-de10-80c6-8c20-dd1c337b02a6
title: 'Cheapest Flights Within k Stops '
created_time: 2025-04-20T17:18:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Cheapest Flights Within k Stops '

---

### Problem Summary:

You're given `flights[i] = [u, v, w]`, meaning a flight from `u → v` costs `w`.

Find the **cheapest cost** from `src` to `dst` using **at most** **`K`** **stops**.

If no such route exists, return `-1`.

***

### 🚦 Difference from Normal Dijkstra:

*   Instead of just minimizing cost, you must also **track number of stops**.

*   Classic Dijkstra doesn't account for such constraints — so we need a **modified BFS with a priority queue**.

***

### 🔧 Approach:

*   Build a **graph** from input.

*   Use a **min-heap** storing `(cost, city, stops)`

*   Keep visiting cheaper paths first, but **only if stops ≤ K**

*   Track the **minimum cost** to each `(city, stops)` combination

***

### ✅ Code:

```python
python
CopyEdit
import heapq
from collections import defaultdict

def findCheapestPrice(n, flights, src, dst, k):
    graph = defaultdict(list)
    for u, v, w in flights:
        graph[u].append((v, w))

    heap = [(0, src, 0)]  # (cost, city, stops)

    while heap:
        cost, node, stops = heapq.heappop(heap)
        if node == dst:
            return cost
        if stops <= k:
            for nei, price in graph[node]:
                heapq.heappush(heap, (cost + price, nei, stops + 1))

    return -1


```

***

### 🧠 Key Insight:

We still use the min-heap like Dijkstra, but include `stops` as part of the state.

### Time Complexity: **O(K \* E)**

Let’s break that down:

*   Each flight is an edge → total of **E = len(flights)**

*   In the **worst case**, for each stop level (from 0 to K), we may process **each edge once**, because:

    *   You can revisit the same city with different number of stops.

    *   And priority queue may contain multiple entries for the same city but with different stops.

*   So we push up to **K \* E** entries into the priority queue (heap).

⏱ **Heap operations** (`heappush` and `heappop`) take **log N**, where N is the number of elements in the heap, which can grow up to **K \* E**, but log factor is generally absorbed in upper bound.

> Final Time Complexity: O(K \* E)

    (More precisely O(K * E * log N), but log factor is typically ignored in Big-O unless you’re comparing Dijkstra vs Bellman-Ford.)

***

### 📦 Space Complexity: **O(V + E)**

*   **Graph storage:** O(E)

*   **Heap:** Can hold up to O(K \* E) elements in worst case (but usually much smaller)

*   **Visited or path tracking (if used):** O(V) or O(V \* K) depending on implementation detail

> Final Space Complexity: O(V + E)
