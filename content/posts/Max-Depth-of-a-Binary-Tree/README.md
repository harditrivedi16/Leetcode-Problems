---
id: 1da7e332-de10-8073-a2db-ddb566406852
title: Max Depth of a Binary Tree
created_time: 2025-04-19T19:31:00.000Z
last_edited_time: 2025-05-01T15:49:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/maximum-depth-of-binary-tree/
my_confidence_level: High
number: 100
june_interviews_prep: null
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Max Depth of a Binary Tree

---

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root: 
            return 0 
        
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))        
```

**Time Complexity:**

```plain text
O(n)
```

, since each node is visited once;

**Space Complexity:**

```plain text
O(h)
```

, due to recursion stack where

*h*

is the height of the tree.
