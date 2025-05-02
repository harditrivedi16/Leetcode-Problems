---
id: 1db7e332-de10-8051-8dbb-f6896f5553eb
title: Symmetric Tree
created_time: 2025-04-20T01:50:00.000Z
last_edited_time: 2025-05-01T15:49:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/symmetric-tree/
my_confidence_level: Meduim
number: 104
amazon_prep: 'No'
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Symmetric Tree

---

```python
def isSymmetric(root: Optional[TreeNode]) -> bool:
    def dfs(t1, t2):
        if not t1 and not t2:
            return True
        if not t1 or not t2 or t1.val != t2.val:
            return False
        return dfs(t1.left, t2.right) and dfs(t1.right, t2.left)
    
    return dfs(root.left, root.right) if root else True

```

**Time Complexity:**

```plain text
O(n)
```

, as each node is checked once;

**Space Complexity:**

```plain text
O(h)
```

, from the recursion stack, where

*h*

is the height of the tree.
