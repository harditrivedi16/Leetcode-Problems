---
id: 1e27e332-de10-8050-9514-c6c5ac2658cb
title: Find Minimum in a rotated sorted array
created_time: 2025-04-27T16:33:00.000Z
last_edited_time: 2025-05-01T14:29:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 8
june_interviews_prep: null
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Find Minimum in a rotated sorted array

---

```python
def findMin(nums):
    left, right = 0, len(nums) - 1

    while left < right:
        mid = (left + right) // 2
        
        if nums[mid] > nums[right]:
            left = mid + 1  # min must be right side
        else:
            right = mid  # min is at mid or left side

    return nums[left]

```

*   **Time Complexity:** O(log n) — We keep halving the search space with each binary search step.

*   **Space Complexity:** O(1) — Only a few pointers (`left`, `right`, `mid`), no extra space used.
