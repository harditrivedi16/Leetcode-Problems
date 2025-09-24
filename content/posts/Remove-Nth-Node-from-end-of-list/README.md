---
id: 1e27e332-de10-809f-9c38-f1a080163cba
title: Remove Nth Node from end of list
created_time: 2025-04-27T20:23:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: High
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: Remove Nth Node from end of list

---

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        # First, find the length of the list
        length = 0
        current = head
        while current:
            length += 1
            current = current.next

        # If the node to remove is the first node
        if length == n:
            return head.next

        # Traverse again to find the (length-n)th node
        current = head
        for _ in range(length - n - 1):
            current = current.next
        
        # Remove the nth node from the end
        current.next = current.next.next
        
        return head

```

### **Explanation:**

*   **Step 1:** We first traverse the list to find the **length** of the list.

*   **Step 2:** We check if the node to be removed is the **head** (i.e., when the length equals `n`).

*   **Step 3:** We then traverse again to find the `(length - n)`th node and update its `next` pointer to skip the nth node from the end.

### **Time Complexity:**

*   **O(L)**: We traverse the list twice (once to find the length and once to remove the node), where `L` is the length of the list.

### **Space Complexity:**

*   **O(1)**: We only use a few extra variables, so the space complexity is constant.
