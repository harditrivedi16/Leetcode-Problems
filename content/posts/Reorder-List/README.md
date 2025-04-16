---
id: 1317e332-de10-8134-9ae0-f3fb69496106
title: Reorder List
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top Interview Questions
  - Neetcode - 150
  - Top 100 Liked Questions
  - Blind 75
problem_link: https://leetcode.com/problems/reorder-list/
my_confidence_level: Meduim
number: 27
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
        slow, fast = head, head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

        second = slow.next
        prev = slow.next = None
        while second:
            tmp = second.next
            second.next = prev
            prev = second
            second = tmp

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

### Recursion

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:

        def rec(root: ListNode, cur: ListNode) -> ListNode:
            if not cur:
                return root
            root = rec(root, cur.next)

            if not root:
                return None
            tmp = None
            if root == cur or root.next == cur:
                cur.next = None
            else:
                tmp = root.next
                root.next = cur
                cur.next = tmp
            return tmp
            
        head = rec(head, head.next)
```

*   Time complexity: *O*(*n*)

    **O(n)**

*   Space complexity: *O*(*n*)

    **O(n)**
