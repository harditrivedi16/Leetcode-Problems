---
id: 2777e332-de10-80d7-a324-f875dd650c75
title: Delete Leaves with a given value
created_time: 2025-09-23T15:10:00.000Z
last_edited_time: 2025-09-23T15:15:00.000Z
difficulty_level: 'Meduim '
number: 12
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/delete-leaves-with-a-given-value/description/
my_confidence_level: High
last_solved: 2025-09-23T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked:
  - none
problem_name: Delete Leaves with a given value

---

### **Problem Restatement**

You’re given the root of a binary tree and an integer `target`.

You need to remove all leaf nodes with value equal to `target`.

⚠️ Important: after removing a leaf, its parent might *become* a new leaf with the same value, so you must check recursively until no such leaves remain.

***

### **Intuition**

*   Use **postorder DFS** (process children before the parent).

*   Recurse into left and right subtrees.

*   After fixing children, check if the current node is a leaf and matches `target`.

*   If yes → return `None` (deletes this node).

*   Else → return the node itself.

***

### **Code**

```python
class Solution:
    def removeLeafNodes(self, root: Optional[TreeNode], target: int) -> Optional[TreeNode]:
        if not root:
            return None

        root.left = self.removeLeafNodes(root.left, target)
        root.right = self.removeLeafNodes(root.right, target)

        if not root.left and not root.right and root.val == target:
            return None
        return root


```

***

### **Complexity**

*   **Time:** O(N) → visit every node once.

*   **Space:** O(h) recursion stack → O(log N) balanced tree, O(N) skewed tree.
