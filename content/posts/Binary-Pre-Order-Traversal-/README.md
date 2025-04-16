---
id: 1317e332-de10-8134-b661-d007c43ba22b
title: 'Binary Pre Order Traversal '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/binary-tree-preorder-traversal/
my_confidence_level: Meduim
number: 24
last_solved: 2025-03-19T00:00:00.000Z
concept_involved:
  - Binary Trees
  - DFS
companies_asked:
  - Bloomberg
  - Facebook/Meta
  - Microsoft
problem_name: 'Binary Pre Order Traversal '

---

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        '''
        # Recursive solution: 

        res = []

        def preorder(root): 
            if not root: 
                return
            res.append(root.val)
            preorder(root.left)
            preorder(root.right)
        preorder(root)
        return res
        '''

        res = []
        stack = []
        curr = root

        while curr or stack: 
            while curr: 
                res.append(curr.val)
                stack.append(curr.right)
                curr= curr.left
            curr = stack.pop() if stack else None
        return res 

        
```

**Time Complexity** (both recursive and iterative): O(n)O(n)O(n), where nnn is the number of nodes in the tree, as each node is visited exactly once.

**Space Complexity**:

*   **Recursive**: O(h), where h is the height of the tree, due to the recursive call stack.

    O(h)O(h)

    hh

*   **Iterative**: O(h), as the stack is used to store nodes up to the depth of the tree, with h being the maximum height of the tree.

    O(h)O(h)

    hh
