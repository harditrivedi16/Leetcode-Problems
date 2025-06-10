---
id: 1e37e332-de10-807f-820e-f2024744ef08
title: Validate BST
created_time: 2025-04-28T15:14:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-04-28T00:00:00.000Z
concept_involved:
  - BST
companies_asked: []
problem_name: Validate BST

---

### **Problem Statement**:

Given a **binary tree**, determine if it is a **valid binary search tree (BST)**. For a tree to be a BST:

*   The **left subtree** of a node contains only nodes with values **less than** the node's value.

*   The **right subtree** of a node contains only nodes with values **greater than** the node's value.

*   Both the **left and right subtrees** must also be binary search trees.

### **Intuition**:

*   A **valid BST** must follow the property that the **values of nodes** on the left side are **less than** the node's value, and on the **right side** are **greater** than the node's value.

*   For each node, we need to ensure that the value of the node lies within a **valid range**. This valid range is determined by the node’s **ancestors**.

    *   For the left child of a node, the maximum allowed value is the value of its parent.

    *   For the right child, the minimum allowed value is the value of its parent.

*   We can use **recursive DFS** with **range constraints** to check this property at each node.

### **Approach**:

*   Perform a **recursive DFS** on the tree, passing a valid range for each node.

*   For each node:

    *   Check if the node's value is within the valid range.

    *   For the left child, the valid range becomes `(min, node.val)`.

    *   For the right child, the valid range becomes `(node.val, max)`.

***

### **Code**:

```python
python
CopyEdit
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def isValidBST(root):
    def dfs(node, low=float('-inf'), high=float('inf')):
        # Base case: if the node is None, it's a valid BST by definition
        if not node:
            return True

        # Check if the node's value is within the valid range
        if not (low < node.val < high):
            return False

        # Recursively check the left and right subtrees with updated ranges
        return dfs(node.left, low, node.val) and dfs(node.right, node.val, high)

    return dfs(root)


```

***

### **Time Complexity**:

*   **O(n)**, where `n` is the number of nodes in the tree.

    *   We visit each node exactly once during the DFS traversal, and for each node, we perform constant-time checks and comparisons.

### **Space Complexity**:

*   **O(h)**, where `h` is the height of the tree.

    *   The space complexity is due to the recursive call stack in the DFS. In the worst case (unbalanced tree), it will be **O(n)**. For a balanced tree, it will be **O(log n)**.
