---
id: 1df7e332-de10-80c2-b3c5-fe496d195785
title: Construct a Binary Tree from InOrder and Pre Order traversal
created_time: 2025-04-24T22:02:00.000Z
last_edited_time: 2025-04-27T19:32:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/
my_confidence_level: High
number: 134
amazon_prep: 'Yes'
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Construct a Binary Tree from InOrder and Pre Order traversal

---

```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        inorder_index = {val: idx for idx, val in enumerate(inorder)}
        self.pre_idx = 0

        def helper(in_left, in_right):
            if in_left > in_right:
                return None
            
            # Pick root from preorder using self.pre_idx
            root_val = preorder[self.pre_idx]
            self.pre_idx += 1
            root = TreeNode(root_val)

            index = inorder_index[root_val]

            root.left = helper(in_left, index - 1)
            root.right = helper(index + 1, in_right)

            return root

        return helper(0, len(inorder) - 1)

```

### Intuition:

To construct a binary tree from **inorder** and **preorder** traversals:

*   The first element in **preorder** is always the root of the tree.

*   Once we identify the root, we can find its index in **inorder**. This divides the tree into:

    *   Left subtree: All elements to the left of the root in **inorder**.

    *   Right subtree: All elements to the right of the root in **inorder**.

*   Recursively apply the same process to build the left and right subtrees, using **preorder** and **inorder** for each.

### Explanation:

*   We start by creating a hashmap **inorder\_index** that maps each element of **inorder** to its index for efficient lookups.

*   The **helper** function is recursively used to build the tree:

    *   The root of the tree is always the first element in the **preorder** array (using the current `pre_left` index).

    *   For the left and right subtrees, we identify the ranges in both the **preorder** and **inorder** arrays by using the root’s index in **inorder**.

*   The recursion continues until the left index exceeds the right index, at which point the recursion terminates.

*

### Time and Space Complexity:

*   **Time Complexity**: O(n) — We make one pass through the **preorder** and **inorder** arrays, and the lookup for each root in the **inorder\_index** hashmap is O(1). Thus, the total time complexity is linear.

*   **Space Complexity**: O(n) — We store the **inorder\_index** hashmap which requires O(n) space, and the recursion stack may also require O(n) space in the worst case (e.g., if the tree is skewed).

### One-liner Summary for How Parameters Are Passed

Problem Type|Helper Params|Why|One-liner recursive parameter logic
\---|---|---|---
Pre + In|`in_left, in_right`|Preorder gives root, use inorder to split left/right|Left: `helper(in_left, index - 1)`Right: `helper(index + 1, in_right)`
Post + In|`in_left, in_right`|Postorder gives root, use inorder to split|Right first: `helper(index + 1, in_right)`Then left: `helper(in_left, index - 1)`
Pre + Post|`pre_left, pre_right, post_left, post_right`|No inorder: need full control of ranges|`root.left = helper(pre_left + 1, pre_left + left_subtree_size, post_left, left_root_index_in_post)
            root.right = helper(pre_left + left_subtree_size + 1, pre_right, left_root_index_in_post + 1, post_right - 1)`
