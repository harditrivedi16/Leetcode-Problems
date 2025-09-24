---
id: 2777e332-de10-80c0-8c0c-cbd170ebbd9a
title: Subtree of Another Tree
created_time: 2025-09-23T15:01:00.000Z
last_edited_time: 2025-09-23T15:03:00.000Z
difficulty_level: Easy
number: 10
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Neetcode 250
problem_link: https://leetcode.com/problems/subtree-of-another-tree/description/
my_confidence_level: High
last_solved: 2025-09-23T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
problem_name: Subtree of Another Tree

---

```python
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        if not subRoot:
            return True
        if not root:
            return False

        def isSame(p, q):
            if not p and not q:
                return True
            if not p or not q:
                return False
            return (p.val == q.val 
                    and isSame(p.left, q.left) 
                    and isSame(p.right, q.right))

        if isSame(root, subRoot):
            return True
        return self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)

```

Complexity
Time: O(m \* n) in the worst case (for each node in root, you may compare against up to subRoot size).

Space: O(h) for recursion depth (h = height of main tree).
