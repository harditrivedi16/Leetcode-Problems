---
id: 1e27e332-de10-804f-8114-fc5d25103066
title: Inorder Successor of Node in BST
created_time: 2025-04-27T20:37:00.000Z
last_edited_time: 2025-04-28T14:52:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 166
amazon_prep: 'Yes'
last_solved: 2025-04-28T00:00:00.000Z
concept_involved:
  - BST
  - Binary Trees
companies_asked: []
problem_name: Inorder Successor of Node in BST

---

```python
def inorderSuccessor(root, p):
    if p.right:
        p = p.right
        while p.left:
            p = p.left
        return p
    
    successor = None
    while root:
        if p.val < root.val:
            successor = root
            root = root.left
        elif p.val > root.val:
            root = root.right
        else:
            break
    return successor

```

In order successor:

In a **BST**, the **inorder successor** of a node is the node with the **smallest key greater than** the key of the given node.
In simpler terms, it’s the **next node** you would visit if you were doing an **inorder traversal** (left → root → right).

*   If the node has a **right child**, the successor is the **leftmost node** in the right subtree.

*   If the node **doesn’t have a right child**, the successor is one of its ancestors — specifically, the **lowest ancestor for which the node would be in the left subtree**.

**Time Complexity:**

*   O(h), where `h` is the height of the tree (O(log n) for balanced BST, O(n) for skewed trees).

**Space Complexity:**

*   O(1) if iterative (as above).
