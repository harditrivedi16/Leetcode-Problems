---
id: 1e47e332-de10-8014-9027-e2fb279b92fb
title: All Nodes Distance K in a Binary Tree
created_time: 2025-04-29T16:19:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: All Nodes Distance K in a Binary Tree

---

**Problem Statement:**

You are given the `root` of a binary tree, a target node, and an integer `k`. Return a list of the values of all nodes that have a distance `k` from the target node.

**Distance** between two nodes is defined as the number of edges in the shortest path between them.

```python
from collections import defaultdict, deque

class Solution:
    def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
        # Step 1: Build graph
        graph = defaultdict(list)

        def buildGraph(node, parent):
            if not node:
                return
            if parent:
                graph[node.val].append(parent.val)
                graph[parent.val].append(node.val)
            buildGraph(node.left, node)
            buildGraph(node.right, node)

        buildGraph(root, None)

        # Step 2: BFS from target
        visited = set()
        queue = deque()
        queue.append((target.val, 0))
        visited.add(target.val)

        res = []

        while queue:
            node, dist = queue.popleft()
            if dist == k:
                res.append(node)
            elif dist < k:
                for neighbor in graph[node]:
                    if neighbor not in visited:
                        visited.add(neighbor)
                        queue.append((neighbor, dist + 1))
        return res

```

### **Intuition:**

This is a graph traversal problem disguised as a tree problem.

Since binary trees are directed (parent to child), and we need to explore **both upward and downward**, we convert the tree into an **undirected graph** using an adjacency list. Once we have the graph, we do a **BFS starting from the target node** until we reach distance `k`.

### **Time & Space Complexity:**

*   **Time Complexity**: O(n)

    Building the graph and BFS both take O(n), where `n` is the number of nodes in the tree.

*   **Space Complexity**: O(n)

    For the adjacency list, visited set, and the queue.
