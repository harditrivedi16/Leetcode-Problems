---
id: 1317e332-de10-81c4-8f12-f4f4bfa4e4a7
title: 'Binary Post Order Traversal '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/binary-tree-postorder-traversal/
my_confidence_level: Meduim
number: 25
last_solved: 2025-03-19T00:00:00.000Z
concept_involved:
  - Binary Trees
  - DFS
companies_asked:
  - Google
  - Facebook/Meta
  - Amazon
  - Bloomberg
problem_name: 'Binary Post Order Traversal '

---

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
        # Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = [] 
        stack = [] 
        curr = root 

        while stack or curr: 
            while curr: 
                res = [curr.val] + res
                stack.append(curr.left)
                curr= curr.right
            
            curr= stack.pop() if stack else None
        return res
            
        
```

**Time Complexity** (both recursive and iterative): O(n)O(n)O(n), where nnn is the number of nodes in the tree, as each node is visited exactly once.

**Space Complexity**:

*   **Recursive**: O(h), where h is the height of the tree, due to the recursive call stack.

    O(h)O(h)

    hh

*   **Iterative**: O(h), as the stack and `visit` list are used to store nodes and their states, with h being the maximum height of the tree.

    O(h)O(h)

    hh
