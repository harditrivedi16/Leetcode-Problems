---
id: 1e27e332-de10-806c-842e-c67c535e71f8
title: Find the Duplicate Number
created_time: 2025-04-27T20:49:00.000Z
last_edited_time: 2025-04-27T20:50:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 165
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: Find the Duplicate Number

---

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        # Phase 1: Finding the intersection point in the cycle
        slow = nums[0]
        fast = nums[0]
        
        while True:
            slow = nums[slow]  # Move slow pointer by 1 step
            fast = nums[nums[fast]]  # Move fast pointer by 2 steps
            if slow == fast:
                break  # We found the intersection point

        # Phase 2: Find the entry point of the cycle (duplicate number)
        slow = nums[0]  # Start slow pointer from the beginning
        while slow != fast:
            slow = nums[slow]  # Move slow pointer by 1 step
            fast = nums[fast]  # Move fast pointer by 1 step

        return slow  # The duplicate number

```

### Intuition:

*   **Phase 1 (Cycle detection):** We use two pointers (slow and fast). The fast pointer moves twice as fast as the slow pointer. When a cycle is present, they will eventually meet at some point within the cycle.

*   **Phase 2 (Finding the entry point of the cycle):** Once the slow and fast pointers meet, we move the slow pointer back to the start of the array and continue both pointers at the same pace. The point where they meet again is the duplicate number.

### Time Complexity:

*   **O(n):** Both the slow and fast pointers traverse the array at most twice. So the time complexity is linear with respect to the number of elements.

### Space Complexity:

*   **O(1):** We only use two extra pointers, so the space complexity is constant, i.e., O(1).

Let me know when you're ready for the next problem!
