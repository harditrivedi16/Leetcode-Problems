---
id: 1e37e332-de10-802c-b83b-cb7b1a9e9588
title: Trim a BST
created_time: 2025-04-28T14:58:00.000Z
last_edited_time: 2025-04-28T15:01:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 168
amazon_prep: 'Yes'
last_solved: 2025-04-28T00:00:00.000Z
concept_involved:
  - Binary Trees
  - BST
companies_asked: []
problem_name: Trim a BST

---

```python
python
CopyEdit
def trimBST(root, low, high):
    if not root:
        return None

    # If current node is smaller than low, discard the left subtree and process the right subtree
    if root.val < low:
        return trimBST(root.right, low, high)

    # If current node is larger than high, discard the right subtree and process the left subtree
    if root.val > high:
        return trimBST(root.left, low, high)

    # Node is within the range, so recursively trim both left and right subtrees
    root.left = trimBST(root.left, low, high)
    root.right = trimBST(root.right, low, high)

    return root


```

### **Intuition:**

To **trim a BST**, we need to:

*   **Remove nodes** that are **less than** **`low`** or **greater than** **`high`**.

*   If the node is **within the range** (`low ≤ node.val ≤ high`), keep it, and recursively trim both left and right subtrees.

*   **If the current node is less than** **`low`**, then we know all the values in the left subtree will also be less than `low`. So, we just **return the right subtree**.

*   **If the current node is greater than** **`high`**, all the values in the right subtree will be greater than `high`. So, we just **return the left subtree**.

*   If the node is within the range, recursively trim both its left and right subtrees.

***

### **Code:**

***

### **Time Complexity:**

*   **O(n)**, where `n` is the number of nodes in the BST.

    In the worst case, we need to visit all nodes to check whether they are within the range and trim accordingly.

### **Space Complexity:**

*   **O(h)**, where `h` is the height of the tree (for recursive calls).

    In the worst case, this can be **O(n)** if the tree is unbalanced (like a linked list). Otherwise, it’s **O(log n)** for a balanced tree.
