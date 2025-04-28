---
id: 1dd7e332-de10-8002-a8c0-e56ac3c5a3a1
title: 'Linked List Cycle I '
created_time: 2025-04-22T16:59:00.000Z
last_edited_time: 2025-04-27T20:19:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/linked-list-cycle/
my_confidence_level: High
number: 118
amazon_prep: 'Yes'
last_solved: 2025-04-22T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: 'Linked List Cycle I '

---

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def hasCycle(head: ListNode) -> bool:
    slow = head
    fast = head

    while fast and fast.next:
        slow = slow.next           # Move slow by 1
        fast = fast.next.next      # Move fast by 2

        if slow == fast:
            return True            # Cycle detected

    return False                   # No cycle

```

### Time Complexity

*   **O(n)** — Each pointer travels at most `n` steps.

### 🧠 Space Complexity

*   **O(1)** — Constant space used (no extra memory).
