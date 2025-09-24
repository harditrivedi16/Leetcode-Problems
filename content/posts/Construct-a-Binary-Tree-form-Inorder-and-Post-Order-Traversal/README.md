---
id: 1df7e332-de10-8083-b7b3-e0121f53e94d
title: Construct a Binary Tree form Inorder and Post Order Traversal
created_time: 2025-04-24T21:51:00.000Z
last_edited_time: 2025-05-01T15:49:00.000Z
difficulty_level: 'Meduim '
remarks: remember the sequence of in order, pre order and post order
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/
my_confidence_level: High
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: Construct a Binary Tree form Inorder and Post Order Traversal

---

```python
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> Optional[TreeNode]:
        if not inorder or not postorder:
            return None

        inorder_index = {val: idx for idx, val in enumerate(inorder)}

        def helper(in_left, in_right):
            if in_left > in_right:
                return None

            root_val = postorder.pop()
            root = TreeNode(root_val)

            index = inorder_index[root_val]
            root.right = helper(index + 1, in_right)
            root.left = helper(in_left, index - 1)

            return root

        return helper(0, len(inorder) - 1)

```

The problem involves constructing a binary tree from two traversal arrays: **inorder** and **postorder**. The key intuition is that in **postorder**, the last element represents the root of the tree or subtree. Using this root, we can split the **inorder** array into two parts: the left and right subtrees. Recursively repeat this process for both subtrees until the tree is fully constructed. This approach leverages the structure of the traversals to build the tree step by step.

Time and Space

*   **Time**: O(n), each node processed once.

*   **Space**: O(n) for hashmap + recursion stack (worst case height `n`).

### One-liner Summary for How Parameters Are Passed

Problem Type|Helper Params|Why|One-liner recursive parameter logic
\---|---|---|---
Pre + In|`in_left, in_right`|Preorder gives root, use inorder to split left/right|Left: `helper(in_left, index - 1)`Right: `helper(index + 1, in_right)`
Post + In|`in_left, in_right`|Postorder gives root, use inorder to split|Right first: `helper(index + 1, in_right)`Then left: `helper(in_left, index - 1)`
Pre + Post|`pre_left, pre_right, post_left, post_right`|No inorder: need full control of ranges|`root.left = helper(pre_left + 1, pre_left + left_subtree_size, post_left, left_root_index_in_post)
            root.right = helper(pre_left + left_subtree_size + 1, pre_right, left_root_index_in_post + 1, post_right - 1)`
