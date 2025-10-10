---
id: 1da7e332-de10-806c-b893-d7999276c594
title: Diameter of Binary Tree
created_time: 2025-04-19T19:31:00.000Z
last_edited_time: 2025-09-23T15:26:00.000Z
difficulty_level: Easy
number: 7
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Neetcode 250
problem_link: https://leetcode.com/problems/diameter-of-binary-tree/
my_confidence_level: Meduim
last_solved: 2025-09-23T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked:
  - Amazon
  - Oracle
  - Meta
problem_name: Diameter of Binary Tree

---

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        res = 0

        def dfs(root):
            nonlocal res

            if not root:
                return 0
            left = dfs(root.left)
            right = dfs(root.right)
            res = max(res, left + right)

            return 1 + max(left, right)

        dfs(root)
        return res
```

**Time complexity: O(n)*****O*****(*****n*****)Space complexity: O(h)*****O*****(*****h*****)**

*

*   Time complexity: *O*(*n*)

    **O(n)**

*   Space complexity: *O*(*h*)

    **O(h)**

### What’s happening here

*   `res` is defined **outside** the helper function `dfs`, but still inside the method `diameterOfBinaryTree`.

*   By default, Python treats variables inside a nested function as **local** to that function.

*   Without `nonlocal`, if you wrote `res = max(res, left + right)` inside `dfs`, Python would think you’re creating a **new local variable** **`res`**, not modifying the outer one → leading to an `UnboundLocalError`.

`nonlocal res` tells Python:

> “Don’t create a new local variable here. Use the res that lives in the nearest enclosing scope (the outer function diameterOfBinaryTree).
