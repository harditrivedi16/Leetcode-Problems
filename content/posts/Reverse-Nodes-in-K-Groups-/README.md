---
id: 1dd7e332-de10-8027-9007-fedf17e7b5a6
title: Reverse Nodes in K Groups.
created_time: 2025-04-22T18:15:00.000Z
last_edited_time: 2025-04-22T19:55:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/reverse-nodes-in-k-group/description/
my_confidence_level: Meduim
number: 125
last_solved: 2025-04-22T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: Reverse Nodes in K Groups.

---

```python
def reverseKGroup(head: ListNode, k: int) -> ListNode:
    # Dummy node to handle edge cases smoothly (like changing the head)
    dummy = ListNode(0)
    dummy.next = head
    groupPrev = dummy

    # Internal helper to get the k-th node from a given node
    def getKthNode(curr: ListNode, k: int) -> ListNode:
        while curr and k > 1:
            curr = curr.next
            k -= 1
        return curr

    while True:
        # Get the k-th node ahead from groupPrev.next
        kth = getKthNode(groupPrev.next, k)
        if not kth:
            break  # Fewer than k nodes left, no reversal needed

        groupNext = kth.next  # Node after the current k-group
        prev = groupNext      # Previous pointer for reversal, starts beyond the group
        curr = groupPrev.next # Start of the group to reverse

        # Reverse the k nodes
        while curr != groupNext:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp

        # After reversing:
        # - groupPrev.next is now the end of the reversed group
        # - prev (which is kth) is the new start of the reversed group
        temp = groupPrev.next
        groupPrev.next = kth
        groupPrev = temp  # Move groupPrev to the end of the reversed group for next iteration

    return dummy.next
```

### Intuition:

*   You’re given a linked list, and you need to reverse nodes in groups of `k`.

*   If the remaining nodes are fewer than `k`, **don’t reverse them**.

*   To solve it:

    *   Check if there are at least `k` nodes ahead.

    *   If yes, reverse that group.

    *   Then recursively move to the next `k`group.

This uses a **recursive** or **iterative group reversal** approach.

### ⏱ Time Complexity: `O(n)`

### 🧠 Space Complexity: `O(1)` (fully iterative, no recursion stack)
