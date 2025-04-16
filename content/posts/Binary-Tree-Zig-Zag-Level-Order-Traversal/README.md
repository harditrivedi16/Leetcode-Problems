---
id: 1c07e332-de10-80e0-a971-e68169a465cf
title: Binary Tree Zig-Zag Level Order Traversal
created_time: 2025-03-24T14:47:00.000Z
last_edited_time: 2025-04-15T16:06:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Microsoft Questions
  - Top Interview Questions
problem_link: >-
  https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/
my_confidence_level: Meduim
number: 69
last_solved: 2025-03-24T00:00:00.000Z
concept_involved:
  - Binary Trees
  - BFS
companies_asked:
  - Amazon
  - Microsoft
  - Facebook/Meta
  - Bloomberg
  - Google
problem_name: Binary Tree Zig-Zag Level Order Traversal

---

```python

class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        res = [] 
        q = collections.deque()
        if root:
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
                level =list(reversed(level)) if len(res) % 2 == 1 else level
                res.append(level)
        return res
        
        
```

Time Complexity: O(n)
Space Complexity: O(n/2) at any level max there will be n/2 elements and queue is only filled level by level.
