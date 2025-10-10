---
id: 14d7e332-de10-8040-89b6-f7d22902d0da
title: 'Add two numbers '
created_time: 2024-11-29T17:57:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
  - Top Interview Questions
problem_link: https://leetcode.com/problems/add-two-numbers/
my_confidence_level: Meduim
last_solved: 2024-12-01T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked:
  - Google
  - Amazon
  - Facebook/Meta
  - Microsoft
  - Bloomberg
problem_name: 'Add two numbers '

---

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        dummy = ListNode()
        carry = 0 
        curr= dummy

        while l1 or l2 or carry: 
            v1 = l1.val if l1 else 0 
            v2 = l2.val if l2 else 0 

            val = v1 + v2 + carry

            carry = val // 10 
            val = val % 10 

            curr.next = ListNode(val)
            curr = curr.next

            l1 = l1.next if l1 else None 
            l2 = l2.next if l2 else None
        return dummy.next 
        
```

Time Complexity = O(m + n); m and n are respective lengths of the two lists

Space Complexity= O(1)
