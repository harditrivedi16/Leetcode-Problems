---
id: 1da7e332-de10-80be-8791-e18bac616e3e
title: Invert Binary Tree
created_time: 2025-04-19T19:31:00.000Z
last_edited_time: 2025-09-23T14:41:00.000Z
difficulty_level: Easy
number: 6
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Neetcode 250
problem_link: https://leetcode.com/problems/invert-binary-tree/
my_confidence_level: High
last_solved: 2025-09-23T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
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

**Time complexity: O(n) ; Space complexity: O(n) for recursion stack.**

*   Time complexity: *O*(*n*)

*   Space complexity: *O*(*n*) for recursion stack.

    *   If you invert using recursion, each recursive call goes down one branch at a time.

    *   The recursion stack depth is at most the **height** **`h`** **of the tree**.

    *   So the **extra space** used is **O(h)**.

        *   For a balanced tree: `h = log n` → space = O(log n).

        *   For a skewed tree: `h = n` → space = O(n).
