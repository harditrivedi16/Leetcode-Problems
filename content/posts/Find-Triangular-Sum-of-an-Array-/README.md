---
id: 1df7e332-de10-802c-9cef-d76830e5e742
title: 'Find Triangular Sum of an Array '
created_time: 2025-04-24T18:06:00.000Z
last_edited_time: 2025-04-24T21:29:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/find-triangular-sum-of-an-array/
my_confidence_level: High
number: 130
amazon_prep: 'Yes'
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked: []
problem_name: 'Find Triangular Sum of an Array '

---

```python
class Solution:
    def triangularSum(self, nums: List[int]) -> int:
        # Continue the process while the length of the array is greater than 1
        while len(nums) > 1:
            # Update the array by adding adjacent elements
            for i in range(len(nums) - 1):
                nums[i] = (nums[i] + nums[i + 1]) % 10
            # Remove the last element after the update
            nums.pop()
        # Return the final remaining element
        return nums[0]

```

### Time Complexity:

*   **Time Complexity**: In each pass, you reduce the size of the array by 1. For each iteration, you do `n-1` operations. So, the time complexity is **O(n)**, where `n` is the length of the array.

### Space Complexity:

*   **Space Complexity**: Since the solution updates the array in-place, no additional data structures are used. Therefore, the space complexity is **O(1)**.
