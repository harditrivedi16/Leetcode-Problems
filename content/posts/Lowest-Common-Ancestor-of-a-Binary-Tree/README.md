---
id: 1e47e332-de10-8065-98f4-dd497bae79cc
title: Lowest Common Ancestor of a Binary Tree
created_time: 2025-04-29T16:24:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Lowest Common Ancestor of a Binary Tree

---

### **Problem Statement:**

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes `p` and `q`.

The **lowest common ancestor** is defined as the **lowest node** in the tree that has **both** **`p`** **and** **`q`** **as descendants** (a node can be a descendant of itself).

***

```python
def lowestCommonAncestor(root, p, q):
	  if not root: 
		  return None
		  
    if root == p or root == q:
        return root

    left = lowestCommonAncestor(root.left, p, q)
    right = lowestCommonAncestor(root.right, p, q)

    if left and right:
        return root  # This node is the LCA
    return left or right

```

### **Intuition:**

This is a classic bottom-up recursion problem.

*   Traverse the tree.

*   If you reach either `p` or `q`, return that node.

*   At each node, check the left and right subtrees:

    *   If both return a non-null value, current node is the LCA.

    *   If only one is non-null, propagate that upward.

**"If we already found the answer (LCA = 2), why don't we just return it and stop?"**

### Here's why we need to **propagate the result upwards** instead of returning immediately:

*   **Recursive functions don’t “know” where they are in the tree globally**.

    When `node 2` finds both `7` and `4`, it returns itself (`2`) — but the actual call that the *user* made was at the **root node**, `3`. The root needs to return the final answer because the **entire recursive call chain must return the answer all the way back to the top**.

*   **The result must reach the original caller**.

### **Time & Space Complexity:**

*   **Time**: O(n) — You traverse every node once.

*   **Space**: O(h) — Due to recursion stack, where `h` is the height of the tree.
