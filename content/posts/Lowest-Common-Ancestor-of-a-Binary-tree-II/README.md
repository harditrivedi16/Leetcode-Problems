---
id: 1e47e332-de10-804f-8cea-c52b60410772
title: Lowest Common Ancestor of a Binary tree II
created_time: 2025-04-29T16:24:00.000Z
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
problem_name: Lowest Common Ancestor of a Binary tree II

---

Problem Statement:
Given a binary tree (not necessarily a BST), and two nodes p and q, return their lowest common ancestor (LCA).
However, in this variation, either of the two nodes might not be present in the tree.
Return None if either p or q is not found.

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        self.foundP = False
        self.foundQ = False

        def dfs(node):
            if not node:
                return None

            left = dfs(node.left)
            right = dfs(node.right)

            mid = node == p or node == q
            if node == p:
                self.foundP = True
            if node == q:
                self.foundQ = True

            if mid + bool(left) + bool(right) >= 2:
                return node

            return node if mid else left or right

        lca = dfs(root)
        return lca if self.foundP and self.foundQ else None

```

We’ll use postorder DFS traversal to search for p and q in the tree.
If both are found below the same root, that root is their LCA.
we will check if p and q both are found: we use mid and self.foundp and self.foundQ.

### **Why use** **`mid`\*\*\*\*?**

In this solution, `mid` serves to identify if the current node (`node`) is either `p` or `q`. It plays a crucial role in determining if the current node is part of the potential Lowest Common Ancestor (LCA).

*   `mid = node == p or node == q`

*   It simply checks if the current node is either `p` or `q`. If it is, `mid` will be `True`, otherwise `False`.

*   **`mid + bool(left) + bool(right)`**:

    *   This sums up whether we found `p` or `q` in the current node (`mid`), in the left subtree (`bool(left)`), or in the right subtree (`bool(right)`).

    *   The result is an integer:

        *   `0` means neither `p` nor `q` are found in the current node or its subtrees.

        *   `1` means either `p` or `q` is found in the current node, or one of its subtrees.

        *   `2` means both `p` and `q` are found in the current node or its subtrees (could be in both left and right children).

        *   `3` means the current node is `p` or `q`, and both left and right children contain either `p` or `q`.

*   **`>= 2`**:

### **Time Complexity:** `O(n)`

One pass through all nodes.

### 📦 **Space Complexity:** `O(h)`

Where `h` is the height of the tree (due to recursion stack).
