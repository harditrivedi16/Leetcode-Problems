---
id: 1317e332-de10-8134-9ae0-f3fb69496106
title: Reorder List
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top Interview Questions
  - Neetcode - 150
  - Top 100 Liked Questions
  - Blind 75
problem_link: https://leetcode.com/problems/reorder-list/
my_confidence_level: Meduim
last_solved: 2024-11-19T00:00:00.000Z
concept_involved:
  - Linked List
  - Two Pointers
companies_asked:
  - Amazon
  - Facebook/Meta
  - TicTok
  - Microsoft
  - Bloomberg
problem_name: Reorder List

---

### Divide-Reverse-Merge

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
    # Reach to the half of the list (median)
        slow, fast = head, head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
#Reversing the second half of the list 
        second = slow.next
        prev = slow.next = None
        while second:
            tmp = second.next
            second.next = prev
            prev = second
            second = tmp
# Merging the two list. 
        first, second = head, prev
        while second:
            tmp1, tmp2 = first.next, second.next
            first.next = second
            second.next = tmp1
            first, second = tmp1, tmp2
```

*   Time complexity: *O*(*n*)

    **O(n)**

*   Space complexity: *O*(1)

    **O(1)**

The task is to reorder a linked list in a specific way:

*   Given a linked list: `L0 -> L1 -> L2 -> ... -> Ln-1 -> Ln`

*   You need to reorder it like this: `L0 -> Ln -> L1 -> Ln-1 -> L2 -> Ln-2 -> ...`

This can be broken down into three main steps:

*   **Find the middle of the linked list** (using the **slow-fast pointer technique**):

    *   Use two pointers: one moving one step at a time (slow), and the other moving two steps at a time (fast).

    *   When `fast` reaches the end, `slow` will be at the middle of the list.

*   **Reverse the second half of the list**:

    *   Once you have the middle, reverse the second half of the list starting from `slow.next`.

    *   This will allow us to access the last nodes of the list in reverse order.

*   **Merge the two halves**:

    *   After reversing the second half, alternate nodes between the first half and the reversed second half.

    *   For example, take the first node of the first half, then the first node of the reversed second half, then the second node of the first half, and so on.
