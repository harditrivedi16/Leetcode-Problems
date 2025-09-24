---
id: 1e47e332-de10-809c-92e5-d0c9b431f411
title: Lowest Common Ancestor of a Binary Search Tree
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
  - BST
companies_asked: []
problem_name: Lowest Common Ancestor of a Binary Search Tree

---

Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes p and q.
The LCA of two nodes p and q in a BST is the lowest node in the tree that has both p and q as descendants (a node can be a descendant of itself).

```python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def lowestCommonAncestor(self, root: TreeNode, p: TreeNode, q: TreeNode) -> TreeNode:
        if p.val < root.val and q.val < root.val:
            return self.lowestCommonAncestor(root.left, p, q)
        elif p.val > root.val and q.val > root.val:
            return self.lowestCommonAncestor(root.right, p, q)
        else:
            return root

```

🧠 Intuition:
Use the properties of BST:

If both p and q are smaller than the current node, LCA must be in the left subtree.

If both are greater, LCA must be in the right subtree.

If the current node splits the two (i.e., one on left, one on right, or one is equal to current), then this node is the LCA.

⏱️ Time Complexity:
O(h) — where h is the height of the BST (in the worst case, O(n) for a skewed tree).

🗂️ Space Complexity:
O(h) for recursive stack (worst O(n) for skewed BST)
