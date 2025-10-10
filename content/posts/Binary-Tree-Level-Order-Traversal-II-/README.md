---
id: 1c07e332-de10-80c0-a966-d3c61807c42f
title: 'Binary Tree Level Order Traversal II '
created_time: 2025-03-24T15:05:00.000Z
last_edited_time: 2025-05-01T15:44:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/
my_confidence_level: High
last_solved: 2025-03-24T00:00:00.000Z
concept_involved:
  - Binary Trees
  - BFS
companies_asked:
  - Amazon
problem_name: 'Binary Tree Level Order Traversal II '

---

```python
class Solution:
    def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
        res = []
        q = collections.deque()
        q.append(root)

        while q: 
            qLen = len(q)
            level = []
            for i in range(qLen): 
                node = q.popleft()
                if node: 
                    level.append(node.val)
                    q.append(node.left)
                    q.append(node.right)
            if level: 
                res.append(level)
        return list(reversed(res))
```

Given the root of a binary tree, return the **bottom-up level order traversal** of its nodes' values. (i.e., from leaf to root, level by level).

Time Complexity: O(n)
Space Complexity: O(n/2) at any level max there will be n/2 elements and queue is only filled level by level.
