---
id: 1dd7e332-de10-8099-b27a-d5239fec291d
title: Intersection of two Linked list
created_time: 2025-04-22T18:13:00.000Z
last_edited_time: 2025-04-24T16:50:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/linked-list-cycle-ii/
my_confidence_level: Meduim
number: 120
amazon_prep: 'No'
last_solved: 2025-04-22T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: Intersection of two Linked list

---

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def getIntersectionNode(headA: ListNode, headB: ListNode) -> ListNode:
    if not headA or not headB:
        return None

    p1 = headA
    p2 = headB

    while p1 != p2:
        p1 = p1.next if p1 else headB
        p2 = p2.next if p2 else headA

    return p1  # Either the intersection node or None

```

If two linked lists intersect, the intersection must happen **after equalizing the remaining lengths**. So, we can use two pointers and switch them to the other list when they reach the end.

### ⏱ Time Complexity:

*   **O(m + n)** — m and n are lengths of the two lists.

### 🧠 Space Complexity:

*   **O(1)** — No extra memory used.
