# Binary Post Order Traversal

Companies asked : Amazon, Bloomberg, Facebook/Meta, Google
Concept involved: Binary Trees, DFS
Difficulty level: Easy
Last Solved : October 28, 2024
My Confidence Level : Meduim
Number: 25
Problem Link: https://leetcode.com/problems/binary-tree-postorder-traversal/

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        """
        # Recursive Approach: 
        res = []

        def postOrder(root): 
            if not root: 
                return 
            postOrder(root.left)
            postOrder(root.right)
            res.append(root.val)

        postOrder(root)
        return res
        """ 

        # Iterative Approach
        res = [] 
        stack, visit = [root], [False]

        while stack: 
            curr, v = stack.pop(), visit.pop()

            if curr: 
                if v: 
                    res.append(curr.val)
                else: 
                    stack.append(curr)
                    visit.append(True)
                    stack.append(curr.right)
                    visit.append(False)
                    stack.append(curr.left)
                    visit.append(False)
        return res 
```

**Time Complexity** (both recursive and iterative): O(n)O(n)O(n), where nnn is the number of nodes in the tree, as each node is visited exactly once.

**Space Complexity**:

- **Recursive**: O(h), where h is the height of the tree, due to the recursive call stack.
    
    O(h)O(h)
    
    hh
    
- **Iterative**: O(h), as the stack and `visit` list are used to store nodes and their states, with h being the maximum height of the tree.
    
    O(h)O(h)
    
    hh