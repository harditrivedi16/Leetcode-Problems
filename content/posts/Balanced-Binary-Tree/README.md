---
id: 1da7e332-de10-80af-9bb2-e2e1fe94d6f0
title: Balanced Binary Tree
created_time: 2025-04-19T19:31:00.000Z
last_edited_time: 2025-05-01T15:49:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/balanced-binary-tree/description/
my_confidence_level: Meduim
number: 101
amazon_prep: 'No'
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Balanced Binary Tree

---

```python
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        def dfs(root):
            if not root:
                return [True, 0]

            left, right = dfs(root.left), dfs(root.right)
            balanced = left[0] and right[0] and abs(left[1] - right[1]) <= 1
            return [balanced, 1 + max(left[1], right[1])]

        return dfs(root)[0]
```

**Time Complexity:**

```plain text
O(n)
```

, as each node is visited once;

**Space Complexity:**

```plain text
O(h)
```

, due to recursion stack, where

*h*

is the tree height.
