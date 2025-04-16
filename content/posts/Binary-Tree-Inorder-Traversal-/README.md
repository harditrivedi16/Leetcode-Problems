---
id: 1317e332-de10-8107-af60-f4e06669ea05
title: 'Binary Tree Inorder Traversal '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/binary-tree-inorder-traversal/
my_confidence_level: Meduim
number: 23
last_solved: 2025-03-19T00:00:00.000Z
concept_involved:
  - Binary Trees
  - DFS
companies_asked:
  - Google
  - Facebook/Meta
problem_name: 'Binary Tree Inorder Traversal '

---

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

*   **Recursive**: O(h), where h is the height of the tree, due to the call stack.

    O(h)O(h)

    hh

*   **Iterative**: O(h), as it uses a stack to store nodes, with h being the maximum depth (or height) of the tree.

    O(h)O(h)

    hh
