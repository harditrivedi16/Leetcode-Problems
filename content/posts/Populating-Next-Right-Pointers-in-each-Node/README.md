---
id: 1e47e332-de10-80dc-b336-e28ca9780d09
title: Populating Next Right Pointers in each Node
created_time: 2025-04-29T16:14:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Populating Next Right Pointers in each Node

---

```python
class Solution:
    def connect(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None
        
        # Start with the root node.
        level_start = root
        
        while level_start:
            current = level_start
            # Traverse the current level
            while current:
                if current.left:
                    current.left.next = current.right  # Connect left child to right child
                if current.right and current.next:
                    current.right.next = current.next.left  # Connect right child to next left child
                current = current.next  # Move to the next node at the current level
            # Move to the next level
            level_start = level_start.left
        
        return root

```

You are given a **perfect binary tree** where all leaf nodes are at the same level, and every paren has two children. The task is to **populate each next pointer** to point to its next right node. If there is no next right node, the next pointer should be set to `None`.

Initially, all the next pointers are set to `None`.

You need to return the root of the tree after the next pointers have been populated.

**Example:**

Input:

```plain text
markdown
CopyEdit
          1
         / \
        2   3
       / \ / \
      4  5 6  7


```

```plain text
rust
CopyEdit
          1 -> NULL
         /  \
        2 -> 3 -> NULL
       /  \  /  \
      4-> 5->6->7 -> NULL

```

**Intuition:**

For each level, we process each node in the current level, connecting its left child to its right child, and if there’s a `next` node at the current level, we also connect the right child to the next node's left child.

After completing one level (i.e., linking all nodes in that level), move to the next level by setting `level_start` to the left child of the current level's root node.
