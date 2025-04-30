---
id: 1db7e332-de10-8074-b483-f63c6dd0fc66
title: 'Course Schedule I '
created_time: 2025-04-20T17:17:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Course Schedule I '

---

You're given `numCourses` and a list of prerequisite pairs `prerequisites` — can you finish all courses?

Each pair is `[a, b]` → **to take course** **`a`\*\*\*\*, you must first take course** **`b`**

This forms a directed graph: `b → a`

```python
from collections import defaultdict, deque

def canFinish(numCourses, prerequisites):
    graph = defaultdict(list)
    indegree = [0] * numCourses

    for a, b in prerequisites:
        graph[b].append(a)
        indegree[a] += 1

    q = deque([i for i in range(numCourses) if indegree[i] == 0])
    visited = 0

    while q:
        node = q.popleft()
        visited += 1
        for nei in graph[node]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                q.append(nei)

    return visited == numCourses

```

Intuition:

Check if there's a **cycle**.

If there’s a cycle → you **can’t finish** all courses

If it’s a DAG → you **can** finish them (i.e., a valid topological sort exists)

***

### 🧠 Approach (Kahn’s Algorithm):

We don't care about the actual order — just whether it's **possible to process all nodes**.

### Why this works:

*   If all courses can be visited via topological sort → `visited == numCourses`

*   If a cycle exists → some nodes will never reach indegree 0 → `visited < numCourses`

### **Time Complexity**:

*   **Building the graph**:

    *   For each edge in the prerequisites, you update the graph and the indegree array. Since there are `E` edges, this takes **O(E)** time.

*   **Processing the queue**:

    *   Each node gets added to the queue at most once, and each node is processed once. Since there are `V` nodes and `E` edges, the while loop runs **O(V + E)** time (processing nodes and their neighbors).

Thus, the total time complexity is:

*   **O(V + E)**, where `V` is the number of courses (nodes) and `E` is the number of prerequisites (edges).

### 💾 **Space Complexity**:

*   **Graph**:

    *   We use a graph represented as an adjacency list, which requires **O(V + E)** space.

*   **Indegree array**:

    *   We maintain an indegree array of size `V`, so **O(V)** space.

*   **Queue**:

    *   The queue stores nodes with indegree 0, so in the worst case, it could hold all `V` nodes at once (if no prerequisites). This also requires **O(V)** space.

Thus, the total space complexity is:

*   **O(V + E)**, where `V` is the number of courses and `E` is the number of prerequisites.
