# Binary Tree Inorder Traversal

Companies asked : Facebook/Meta, Google
Concept involved: Binary Trees, DFS
Difficulty level: Easy
Last Solved : October 28, 2024
Leetcode Problem List: Top 100 Liked Questions, Top Interview Questions
My Confidence Level : Meduim
Number: 23
Problem Link: https://leetcode.com/problems/binary-tree-inorder-traversal/

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        """
        #Recursive solution
        res = []

        def inorder(root): 
            if not root: 
                return 
            inorder(root.left)
            res.append(root.val)
            inorder(root.right)
        inorder(root)
        return res
        """
        #Iterative solution 
        res = []
        stack = []
        curr = root

        while curr or stack: 
            while curr: 
                stack.append(curr)
                curr = curr.left 
            curr = stack.pop()
            res.append(curr.val)
            curr = curr.right
        return res
        
```

**Time Complexity** (both recursive and iterative): O(n)O(n)O(n), where nnn is the number of nodes in the tree, as each node is visited once.

**Space Complexity**:

- **Recursive**: O(h), where h is the height of the tree, due to the call stack.
    
    O(h)O(h)
    
    hh
    
- **Iterative**: O(h), as it uses a stack to store nodes, with h being the maximum depth (or height) of the tree.
    
    O(h)O(h)
    
    hh