---
id: 1da7e332-de10-80be-8791-e18bac616e3e
title: Invert Binary Tree
created_time: 2025-04-19T19:31:00.000Z
last_edited_time: 2025-04-20T01:54:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/invert-binary-tree/
my_confidence_level: High
number: 89
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Invert Binary Tree

---

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root: return None

        root.left, root.right = root.right, root.left

        self.invertTree(root.left)
        self.invertTree(root.right)

        return root
```

# **Time & Space Complexity**

**Time complexity: O(n)*****O*****(*****n*****)Space complexity: O(n)*****O*****(*****n*****) for recursion stack.**

*   Time complexity: *O*(*n*)

    **O(n)**

*   Space complexity: *O*(*n*) for recursion stack.

    **O(n)**
