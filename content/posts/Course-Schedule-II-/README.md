---
id: 1db7e332-de10-803b-9f52-c820d8b20bbf
title: 'Course Schedule II '
created_time: 2025-04-20T17:17:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: 'Course Schedule II '

---

You are given `numCourses` and a list of `prerequisites`.

Return the **ordering of courses** you should take to finish all courses.

If there are **multiple possible orders**, return **any valid order**.

If it's **impossible** to finish all courses (due to a cycle), return an **empty array**.

***

### 🧠 **Approach (Kahn's Algorithm)**:

Similar to Course Schedule I, but instead of just checking if a valid order is possible, we need to **return the actual order**.

The idea is:

*   **Perform Topological Sort** (Kahn’s algorithm).

*   **Return the result** as the course order.

### **Code**

```python

from collections import defaultdict, deque

def findOrder(numCourses, prerequisites):
    graph = defaultdict(list)
    indegree = [0] * numCourses
    result = []

    for a, b in prerequisites:
        graph[b].append(a)
        indegree[a] += 1

    q = deque([i for i in range(numCourses) if indegree[i] == 0])

    while q:
        node = q.popleft()
        result.append(node)
        for nei in graph[node]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                q.append(nei)

    return result if len(result) == numCourses else []


```

***

### 🔍 Explanation:

*   **Build the graph and indegree array**:

    Same as before — we create an adjacency list and track indegrees.

*   **Queue Initialization**:

    Enqueue all courses with indegree 0 (i.e., courses with no prerequisites).

*   **Process the queue**:

    For each course, add it to the result and reduce the indegree of its neighbors. If any neighbor’s indegree becomes 0, add it to the queue.

*   **Check for cycles**:

    If we’ve processed all `numCourses` in the result, we’ve found a valid order. Otherwise, it means there's a cycle, so return `[]`.

***

### 🕒 **Time Complexity**:

*   **O(V + E)** where:

    *   `V` = number of courses

    *   `E` = number of prerequisites

### 💾 **Space Complexity**:

*   **O(V + E)** for the graph, indegree array, and queue.
