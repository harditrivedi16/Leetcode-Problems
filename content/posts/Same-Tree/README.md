---
id: 1da7e332-de10-809b-a8ca-e187fe4bf0ca
title: Same Tree
created_time: 2025-04-19T19:31:00.000Z
last_edited_time: 2025-04-20T01:30:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/same-tree/
my_confidence_level: High
number: 85
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Same Tree

---

```python
def isSameTree(p, q):
    # Base Case 1: Both nodes are None → trees match here
    if not p and not q:
        return True

    # Base Case 2: One node is None, the other is not → mismatch
    if not p or not q:
        return False

    # Base Case 3: Values mismatch → trees differ
    if p.val != q.val:
        return False

    # Recursive Case: Check left and right subtrees
    return isSameTree(p.left, q.left) and isSameTree(p.right, q.right)

```

*   **Time Complexity:** `O(n)`

    → We visit each node once in both trees (where *n* is the number of nodes in the smaller of the two trees if they're unequal, or in either tree if equal).

*   **Space Complexity:** `O(h)`

    → Due to recursion stack, where *h* is the height of the tree (O(log n) for balanced, O(n) for skewed).
