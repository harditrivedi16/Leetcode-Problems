---
id: 1c07e332-de10-802f-b061-c9ce06eab0c6
title: Binary Tree Level Order Traversal
created_time: 2025-03-24T14:44:00.000Z
last_edited_time: 2025-04-15T16:06:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/binary-tree-level-order-traversal/
my_confidence_level: High
number: 68
last_solved: 2025-03-24T00:00:00.000Z
concept_involved:
  - Binary Trees
  - BFS
companies_asked:
  - Amazon
  - Bloomberg
  - Google
problem_name: Binary Tree Level Order Traversal

---

```python
**class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
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
        return res**
```

Time Complexity: O(n)
Space Complexity: O(n/2) at any level max there will be n/2 elements and queue is only filled level by level.
