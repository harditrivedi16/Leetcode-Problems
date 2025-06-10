---
id: 1e47e332-de10-808c-8ba0-fadcb99e997b
title: Max length of subarray with positive product
created_time: 2025-04-29T15:47:00.000Z
last_edited_time: 2025-05-01T14:41:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 29
june_interviews_prep: null
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked: []
problem_name: Max length of subarray with positive product

---

Max Length of Subarray with a Positive Product:
Given an array of integers nums, find the length of the longest subarray where the product of all elements in the subarray is positive. The array can contain both positive and negative numbers, and you need to find the longest contiguous subarray with a positive product.

```python
class Solution:
    def getMaxLen(self, nums: List[int]) -> int:
        maxLength = 0
        posLen, negLen = 0, 0  # Length of subarray with positive and negative product

        for num in nums:
            if num > 0:
                posLen += 1
                negLen = negLen + 1 if negLen > 0 else 0  # Carry forward negative subarray length if possible
            elif num < 0:
                posLen, negLen = negLen + 1 if negLen > 0 else 0, posLen + 1
            else:
                posLen, negLen = 0, 0  # Reset for 0
            
            maxLength = max(maxLength, posLen)

        return maxLength

```

### Intuition:

This problem requires us to find the length of the longest contiguous subarray in which the product of all elements is positive. The core idea is based on managing two states for each window (subarray) as we move through the list:

*   **posLen**: The length of the subarray where the product of its elements is positive.

*   **negLen**: The length of the subarray where the product of its elements is negative.

### Key Steps:

*   **Positive number**: It extends the positive product subarray.

*   **Negative number**: It flips the sign of the product. If there's already a negative product subarray, including this negative number can make the product positive (because negative \* negative = positive), so we swap `posLen` and `negLen`.

*   **Zero**: The product becomes zero, so both `posLen` and `negLen` are reset.

*   **Time Complexity:** O(n)

*   **Space Complexity:** O(1)
