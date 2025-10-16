---
id: 1317e332-de10-81c2-bef7-d084cc5d4619
title: 'Reverse a Linked List '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
difficulty_level: Easy
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Interview Questions
  - Neetcode - 150
  - Blind 75
problem_link: https://leetcode.com/problems/reverse-linked-list/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Linked List
companies_asked:
  - Microsoft
  - Amazon
  - Apple
  - Adobe
  - Bloomberg
  - Facebook/Meta
  - Google
  - Tcs
  - TicTok
problem_name: 'Reverse a Linked List '

---

Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

There is two possible solution: one iteratively with two pointers and second with recursion.

```python
class Solution:
	def reverseList(self, head) -> [ListNode]:
		prev = None
		curr = head 
		while curr:
			temp = curr.next
			curr.next= prev
			prev = curr
			curr = temp 
			
		return prev
```

Here we simply use two pointers prev and curr, to reverese the

The `reverseList` function iterates through a singly linked list, reversing the node connections by shifting each node's `next` pointer to its previous node. This is achieved using two pointers, `prev` and `curr`, where `prev` trails behind `curr` to hold the new reversed list. The time complexity is O(n) since each node is visited once, and the space complexity is O(1) because only a few extra variables are used, irrespective of the input size.

## Recursive

```python
class Solution:
	def reverseList (self, head: [ListNode])-> [ListNode]:
		if not head or head.next == None:
			return head
		new_Head = self.reverseList(head.next)
		head.next.next = head 
		head.next = none 
		
		return p 
		
```

Let's step through how this function works using your example linked list: `head -> N1 -> N2 -> N3 -> N4`.

### Function Explanation

*   **Base Case**:

    *   If `head` is `None` or `head.next` is `None`, the function returns `head`. This is crucial because:

        *   A `None` head indicates an empty list.

        *   A node without a `next` node indicates the last node in the list, which becomes the new head of the reversed list.

*   **Recursive Case**:

    *   The function calls itself with the next node in the list (`head.next`). This continues until the base case is reached.

### Example Execution with `head -> N1 -> N2 -> N3 -> N4`

*   The recursive function is called starting with `head` pointing to `N1`.

*   **First Level (N1)**:

    *   Recursive call with `head.next` (N2).

*   **Second Level (N2)**:

    *   Recursive call with `head.next` (N3).

*   **Third Level (N3)**:

    *   Recursive call with `head.next` (N4).

*   **Fourth Level (N4)**:

    *   Recursive call with `head.next` (`None`).

    *   Hits the base case, returns `N4` as the new head of the reversed sublist starting from `N4`.

*   **Backtracking to N3**:

    *   `head.next.next = head` sets `N4.next` to `N3` (linking N4 back to N3).

    *   `head.next = None` makes `N3.next` `None` to end the sublist here.

    *   Returns `N4`, the new head up to this point.

*   **Backtracking to N2**:

    *   Similar adjustments make `N3.next` point to `N2`.

    *   Returns `N4`, maintaining it as the head.

*   **Backtracking to N1**:

    *   Reverses the link so `N2.next` points to `N1`.

    *   Returns `N4`.

*   **Complete Reversal**:

    *   Finally, the original `head` (N1) has its `next` set to `None`, confirming it's now the end of the reversed list.

    *   `N4` remains the head of the fully reversed list and is returned by the top-level call.

### Conclusion

The final output for the linked list `head -> N1 -> N2 -> N3 -> N4` after reversal is `head -> N4 -> N3 -> N2 -> N1`. The recursive approach flips the `next` pointers of each node until the original head becomes the tail, and the original tail becomes the head. This recursive method is concise but has a space complexity of O(n) due to the call stack usage for each node, and a time complexity of O(n) as each node is processed once.
