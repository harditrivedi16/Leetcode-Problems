---
id: 1dd7e332-de10-80d9-acbf-f6dcceccc6b1
title: Merge k sorted list
created_time: 2025-04-22T18:15:00.000Z
last_edited_time: 2025-04-27T20:51:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/merge-k-sorted-lists/
my_confidence_level: Meduim
number: 124
amazon_prep: 'Yes'
last_solved: 2025-04-22T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: Merge k sorted list

---

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def mergeKLists(lists: list[ListNode]) -> ListNode:
    if not lists or len(lists) == 0:
        return None

    # Recursive merge sort style divide & conquer
    def mergeLists(left: int, right: int) -> ListNode:
        if left == right:
            return lists[left]
        mid = (left + right) // 2
        l1 = mergeLists(left, mid)
        l2 = mergeLists(mid + 1, right)
        return mergeTwoLists(l1, l2)

    # Recursive helper to merge two sorted linked lists
    def mergeTwoLists(l1: ListNode, l2: ListNode) -> ListNode:
        if not l1 or not l2:
            return l1 or l2
        if l1.val < l2.val:
            l1.next = mergeTwoLists(l1.next, l2)
            return l1
        else:
            l2.next = mergeTwoLists(l1, l2.next)
            return l2

    return mergeLists(0, len(lists) - 1)

```

### Intuition:

*   You're given `k` sorted linked lists. You need to merge them into one **fully sorted list**.

*   This is similar to the **merge step in Merge Sort**.

*   So, use **Divide and Conquer**:

    *   Recursively split the list of lists into halves.

    *   Merge pairs of lists using a helper function (like `mergeTwoLists`).

    *   Combine the results until you're down to one fully merged list.

***

### 🔧 Helper Function: `mergeTwoLists`

(Uses recursion, like the way two lists are merged in merge sort.)

### ⏱ Time Complexity:

*   **O(N log k)** where:

    *   `N` = total number of nodes across all lists,

    *   `k` = number of lists.

*   Each node is processed `log k` times due to divide and conquer merging.

### 🧠 Space Complexity:

*   **O(log k)** for recursion stack in `mergeLists` (not counting output list).

*   **O(1)** auxiliary space in `mergeTwoLists` if converted to iterative.
