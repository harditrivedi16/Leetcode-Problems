---
id: 1dd7e332-de10-807b-ac39-e51dbdae0e0f
title: 'Linked List Cycle II '
created_time: 2025-04-22T18:13:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/linked-list-cycle-ii/
last_solved: null
concept_involved:
  - Linked List
companies_asked: []
problem_name: 'Linked List Cycle II '

---

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def detectCycle(head: ListNode) -> ListNode:
    slow = head
    fast = head

    # First step: detect if a cycle exists
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            break
    else:
        return None  # No cycle

    # Second step: find the start of the cycle
    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next

    return slow  # Start of the cycle

```

### Time Complexity

*   **O(n)** — Full traversal in worst-case.

### 🧠 Space Complexity

*   **O(1)** — No extra memory used.

Let’s say:

*   `L` = distance from `head` to the start of the cycle

*   `C` = length of the cycle

*   `x` = distance from the start of the cycle to the meeting point inside the cycle

At the point where `slow == fast`:

*   `slow` has traveled `L + x`

*   `fast` has traveled `L + x + k*C` for some `k` (since it loops around)

Since `fast` moves 2x speed:

```plain text
ruby
CopyEdit
2(L + x) = L + x + k*C
=> L + x = k*C
=> L = k*C - x


```

So, if you reset `slow` to `head` and move both `slow` and `fast` **one step at a time**, they will meet at the **start of the cycle** after `L` steps.

That’s why the second `while slow != fast:` loop works — it walks both pointers the same distance to the **entry point of the loop**.
