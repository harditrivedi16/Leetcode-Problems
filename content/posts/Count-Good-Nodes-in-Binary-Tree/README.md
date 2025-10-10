---
id: 1bb7e332-de10-802f-9f00-fe6adf50dcd7
title: Count Good Nodes in Binary Tree
created_time: 2025-03-19T13:52:00.000Z
last_edited_time: 2025-09-23T15:09:00.000Z
difficulty_level: 'Meduim '
number: 11
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Neetcode 250
problem_link: https://leetcode.com/problems/count-good-nodes-in-binary-tree/
my_confidence_level: Meduim
last_solved: 2025-09-23T00:00:00.000Z
concept_involved:
  - DFS
  - Binary Trees
companies_asked:
  - Meta
problem_name: Count Good Nodes in Binary Tree

---

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        self.res = 0  # Counter for good nodes

        def dfs(curr, max_so_far):
            if curr is None:
                return
            
            # If the current node is greater than or equal to max_so_far, it's a "good" node
            if curr.val >= max_so_far:
                self.res += 1
                max_so_far = curr.val  # Update the max value along this path
            
            # Recursively call DFS on left and right children
            dfs(curr.left, max_so_far)
            dfs(curr.right, max_so_far)
            
        # Initial call to DFS with root and its value as max_so_far
        dfs(root, root.val)
        return self.res

                
```

### Problem Statement:

Given a binary tree, a **good node** is defined as a node whose value is **greater than or equal to** all the values from the root to that node.

Return the number of **good nodes** in the binary tree.

Time Complexity: O(N)- since we go through each Node once

**2. Space complexity**

There are **two kinds of space** to consider:

*   **Auxiliary variables** (like `res` or `maxSoFar`). That’s O(1).

*   **Recursion stack** from DFS. That depends on tree height `h`.

*   Best case (balanced tree): recursion depth = O(log N).

*   Worst case (skewed tree): recursion depth = O(N).

So the **true space complexity** is:

👉 **O(h)** = O(log N) average, O(N) worst case.
