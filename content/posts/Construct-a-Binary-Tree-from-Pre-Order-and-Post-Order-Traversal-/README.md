---
id: 1df7e332-de10-800b-b55a-fee3ba3b0ded
title: 'Construct a Binary Tree from Pre Order and Post Order Traversal '
created_time: 2025-04-24T21:54:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: 'Meduim '
remarks: >-
  remember order of post, pre and in order, and to make a helper function that
  intakes, pre and post order tree’s first and and last element. basically we
  have to find the root, where left sub tree starts, where right sub tree starts
  etc. 
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/
my_confidence_level: Meduim
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Binary Trees
companies_asked: []
problem_name: 'Construct a Binary Tree from Pre Order and Post Order Traversal '

---

```python
# Definition for a binary tree node.
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def buildTree(self, preorder: List[int], postorder: List[int]) -> TreeNode:
        # Helper function to recursively build the tree
        def helper(pre_left, pre_right, post_left, post_right):
            if pre_left > pre_right:
                return None

            # Root of the current subtree
            root_val = preorder[pre_left]
            root = TreeNode(root_val)

            # Base case: if there's only one node
            if pre_left == pre_right:
                return root

            # Get the root of the left subtree in postorder (next element after the root of the left subtree)
            left_root_val = preorder[pre_left + 1]
            left_root_index_in_post = postorder.index(left_root_val)

            # The number of nodes in the left subtree
            left_subtree_size = left_root_index_in_post - post_left + 1

            # Recursively build the left and right subtrees
            root.left = helper(pre_left + 1, pre_left + left_subtree_size, post_left, left_root_index_in_post)
            root.right = helper(pre_left + left_subtree_size + 1, pre_right, left_root_index_in_post + 1, post_right - 1)

            return root
        
        return helper(0, len(preorder) - 1, 0, len(postorder) - 1)

```

### Intuition:

*   **Preorder** traversal starts with the root, then moves to the left and right subtrees.

*   **Postorder** traversal ends with the root, after visiting the left and right subtrees.

*   Using the root value from **preorder**, we can locate it in the **postorder** array. The elements before it in **postorder** will represent the left subtree, and the elements after it will represent the right subtree.

*   Recursively divide the problem by constructing left and right subtrees until all nodes are added.

**Helper Parameters (Preorder + Postorder):**
We pass four indices: `pre_left`, `pre_right`, `post_left`, `post_right` — representing the current range of preorder and postorder we're building the tree from.
To find the left subtree size, we look for `pre[pre_left + 1]` (left child) in postorder.
The size becomes `index - post_left + 1`.
We do `+1` because both `post_left` and `index` are inclusive — this gives the total number of nodes in the left subtree.

### Time and Space Complexity:

*   **Time Complexity**: O(n^2) because for each node, we find its corresponding index in the **postorder** array (which is O(n)), and this happens for each node.

*   **Space Complexity**: O(n), where n is the number of nodes in the tree. We store the tree nodes and recursion stack.

### One-liner Summary for How Parameters Are Passed

Problem Type|Helper Params|Why|One-liner recursive parameter logic
\---|---|---|---
Pre + In|`in_left, in_right`|Preorder gives root, use inorder to split left/right|Left: `helper(in_left, index - 1)`Right: `helper(index + 1, in_right)`
Post + In|`in_left, in_right`|Postorder gives root, use inorder to split|Right first: `helper(index + 1, in_right)`Then left: `helper(in_left, index - 1)`
Pre + Post|`pre_left, pre_right, post_left, post_right`|No inorder: need full control of ranges|`root.left = helper(pre_left + 1, pre_left + left_subtree_size, post_left, left_root_index_in_post)
            root.right = helper(pre_left + left_subtree_size + 1, pre_right, left_root_index_in_post + 1, post_right - 1)`
