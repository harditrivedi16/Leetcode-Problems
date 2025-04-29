---
id: 1e37e332-de10-802e-b1da-c9d526cc9674
title: kth smallest element in BST
created_time: 2025-04-28T15:09:00.000Z
last_edited_time: 2025-04-28T15:14:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 170
amazon_prep: 'Yes'
last_solved: 2025-04-28T00:00:00.000Z
concept_involved:
  - BST
  - Binary Trees
companies_asked: []
problem_name: kth smallest element in BST

---

### **Problem Statement**:

Given a **binary search tree (BST)**, write a function to find the **kth smallest element** in the BST.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def kthSmallest(root, k):
    # This will store the current count of nodes visited in inorder traversal
    self.count = 0
    self.result = None
    
    def inorder(node):
        # Base case
        if not node:
            return
        
        # Traverse the left subtree
        inorder(node.left)
        
        # Process the current node
        self.count += 1
        if self.count == k:
            self.result = node.val
            return
        
        # Traverse the right subtree
        inorder(node.right)
    
    # Start inorder traversal
    inorder(root)
    
    return self.result

```

### **Intuition**:

*   In a **BST**, the **inorder traversal** (left, root, right) will visit the nodes in **ascending order**.

*   By performing an **inorder traversal** and keeping track of how many nodes we've visited, we can stop as soon as we reach the **kth smallest element**.

So, the approach is:

*   Perform an **inorder traversal** of the BST.

*   As we traverse, maintain a count of how many elements we have passed so far.

*   When the count reaches `k`, we can return that node.

### **Time Complexity**:

*   **O(h + k)**, where `h` is the height of the tree, and `k` is the position of the smallest element we need to find.

    *   The **height** **`h`** accounts for the time taken to reach the leaf nodes.

    *   The **k** is the number of nodes we need to traverse to find the kth smallest.

    *   In the worst case (skewed tree), it can be **O(n)**, where `n` is the number of nodes in the tree.

### **Space Complexity**:

*   **O(h)** for recursion stack, where `h` is the height of the tree.

    *   For a balanced tree, the space complexity is **O(log n)**, while for a skewed tree, it can be **O(n)**.
