---
id: 1db7e332-de10-8039-b789-d358d380f399
title: 'Network Delay Time '
created_time: 2025-04-20T17:18:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
number: null
june_interviews_prep: null
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Network Delay Time '

---

### Problem Summary (Leetcode 743):

You’re given a list of directed edges `times[i] = [u, v, w]`, meaning `u → v` takes `w` time.

You need to compute the **minimum time it takes for all nodes to receive a signal** sent from node `k`.

If **any node is unreachable**, return `-1`.

***

### 📘 Example:

```python
python
CopyEdit
Input:
times = [[2,1,1],[2,3,1],[3,4,1]],
n = 4, k = 2

Output: 2


```

Signal from 2 → 3 → 4 (cost 2), and 2 → 1 (cost 1)

***

### 🔧 Approach (Using Dijkstra):

*   **Build a graph** from the input edge list

*   Use **Dijkstra’s Algorithm** starting from `k`

*   After processing, check the **maximum time** it takes to reach any node

*   If any node is unreachable (still `inf`), return `1`

***

### ✅ Code:

```python
python
CopyEdit
import heapq
from collections import defaultdict

def networkDelayTime(times, n, k):
    graph = defaultdict(list)
    for u, v, w in times:
        graph[u].append((v, w))

    min_heap = [(0, k)]  # (time, node)
    dist = {}  # shortest time to reach each node

    while min_heap:
        time, node = heapq.heappop(min_heap)
        if node in dist:
            continue
        dist[node] = time
        for nei, w in graph[node]:
            if nei not in dist:
                heapq.heappush(min_heap, (time + w, nei))

    return max(dist.values()) if len(dist) == n else -1


```

***

### ⏱ Time & Space:

*   **Time:** O(E log V)

*   **Space:** O(V + E)
