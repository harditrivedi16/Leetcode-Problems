---
id: 1e37e332-de10-80e7-b24b-f80d55acf25b
title: Convert a sorted list to BST
created_time: 2025-04-28T15:01:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 49
june_interviews_prep: null
last_solved: 2025-04-28T00:00:00.000Z
concept_involved:
  - Linked List
  - BST
  - Binary Trees
companies_asked: []
problem_name: Convert a sorted list to BST

---

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def sortedListToBST(head):
    # Function to find the middle of the linked list
    def findMiddle(left, right):
        slow = left
        fast = left
        while fast != right and fast.next != right:
            slow = slow.next
            fast = fast.next.next
        return slow

    # Base case
    if not head:
        return None

    # Find the middle node
    mid = findMiddle(head, None)

    # Create the root node with the middle value
    root = TreeNode(mid.val)

    # Recursively build the left and right subtrees
    if head == mid:  # base case when there’s only one element left
        return root

    # Left subtree: head to mid (not including mid itself)
    left_head = head
    right_head = mid.next
    mid.next = None  # Disconnect the mid node from the rest of the list
    root.left = sortedListToBST(left_head)  # Recurse for left subtree

    # Right subtree: mid.next to end
    root.right = sortedListToBST(right_head)  # Recurse for right subtree

    return root

```

Given a **sorted linked list**, we need to convert it into a **balanced binary search tree (BST)**.

*   **Balanced BST**: A balanced BST ensures that for every node, the height difference between its left and right subtrees is at most 1.

*   To achieve this, the **middle element** of the list will become the **root** of the BST, because in a sorted list, the middle element is always the best choice for keeping the tree balanced.

*   Then, recursively:

    *   The left part of the list will become the left subtree.

    *   The right part of the list will become the right subtree.

### **Time Complexity:**

*   **O(n)**, where `n` is the number of nodes in the linked list.

    *   Each node is processed once when finding the middle element and recursively constructing the tree.

### **Space Complexity:**

*   **O(log n)** for the recursion stack (due to the recursive nature of dividing the list in half).

    *   In the worst case, this would be **O(n)** if the tree is skewed (like a linked list).
