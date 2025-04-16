---
id: 1c07e332-de10-80e0-a6b1-dd3d1e381287
title: Binary Tree Right Side View
created_time: 2025-03-24T15:13:00.000Z
last_edited_time: 2025-04-15T16:06:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Facebook Questions
problem_link: https://leetcode.com/problems/binary-tree-right-side-view/description/
my_confidence_level: High
number: 71
last_solved: 2025-03-24T00:00:00.000Z
concept_involved:
  - Binary Trees
  - BFS
companies_asked:
  - Meta
  - Amazon
  - TicTok
  - Oracle
  - Uber
  - Yandex
  - Google
problem_name: Binary Tree Right Side View

---

```python
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        
        res = []
        q = collections.deque()
        q.append(root)

        while q: 
            qLen = len(q)
            level = collections.deque()
            for i in range(qLen): 
                node = q.popleft()
                if node: 
                    level.append(node.val)
                    q.append(node.left)
                    q.append(node.right)
            if level: 
                res.append(level.pop())
        return res
```

Time Complexity: O(n)
Space Complexity: O(n/2) at any level max there will be n/2 elements and queue is only filled level by level.
