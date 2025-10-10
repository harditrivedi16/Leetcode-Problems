---
id: 1437e332-de10-8094-a563-caeacb85331c
title: Merge Two Sorted List
created_time: 2024-11-19T19:40:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
difficulty_level: Easy
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Blind 75
  - Top 100 Liked Questions
  - Neetcode - 150
  - Top Interview Questions
problem_link: https://leetcode.com/problems/merge-two-sorted-lists/description/
my_confidence_level: High
last_solved: 2025-03-20T00:00:00.000Z
concept_involved:
  - Linked List
  - Recursion
companies_asked:
  - Amazon
  - Google
  - Microsoft
  - Bloomberg
  - Facebook/Meta
  - Yandex
  - HPE
  - Huawei
problem_name: Merge Two Sorted List

---

### Iteration

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def mergeTwoLists(self, list1: ListNode, list2: ListNode) -> ListNode:
        dummy = node = ListNode()

        while list1 and list2:
            if list1.val < list2.val:
                node.next = list1
                list1 = list1.next
            else:
                node.next = list2
                list2 = list2.next
            node = node.next

        node.next = list1 or list2

        return dummy.next
```

*   Time complexity: *O*(*n*+*m*)

    **O(n+m)**

*   Space complexity: *O*(1)

    **O(1)**

> Where n is the length of list1 and m is the length of list2.

### Recursion

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if list1 is None:
            return list2
        if list2 is None:
            return list1
        if list1.val <= list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list1, list2.next)
            return list2
```

*   Time complexity: *O*(*n*+*m*)

    **O(n+m)**

*   Space complexity: *O*(*n*+*m*)

    **O(n+m)**
