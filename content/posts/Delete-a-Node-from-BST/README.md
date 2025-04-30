---
id: 1e37e332-de10-80d7-966c-ebaaeddbbe95
title: Delete a Node from BST
created_time: 2025-04-28T14:52:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-28T00:00:00.000Z
concept_involved:
  - BST
  - Binary Trees
companies_asked: []
problem_name: Delete a Node from BST

---

```python
def deleteNode(root, key):
    if not root:
        return None

    if key < root.val:
        root.left = deleteNode(root.left, key)
    elif key > root.val:
        root.right = deleteNode(root.right, key)
    else:
        # Node found
        if not root.left:
            return root.right
        if not root.right:
            return root.left
        
        # Node has two children
        # Find inorder successor
        successor = root.right
        while successor.left:
            successor = successor.left
        
        root.val = successor.val
        root.right = deleteNode(root.right, successor.val)

    return root

```

**Intuition:**

To delete a node from a **BST**, you have three cases:

*   **Node not found**:

    *   Just return `root` (nothing to do).

*   **Node has only one child** (or no child):

    *   Replace the node with its child (or `None`).

*   **Node has two children**:

    *   Find the **inorder successor** (smallest value in the right subtree).

    *   Replace node’s value with successor’s value.

    *   Then **delete** that successor node from the right subtree.

This way, BST properties stay intact.

**Time Complexity:**

*   **O(h)**, where `h` is height of tree (O(log n) for balanced BST, O(n) for skewed tree).

**Space Complexity:**

*   **O(h)** recursion stack (because of recursive calls).

***
