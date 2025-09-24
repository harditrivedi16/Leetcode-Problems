---
id: 1e27e332-de10-80bf-9d52-d030ea624998
title: Find Minimum in a rotated sorted array - II
created_time: 2025-04-27T16:39:00.000Z
last_edited_time: 2025-05-01T14:29:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Find Minimum in a rotated sorted array - II

---

```python
def findMin(nums):
    left, right = 0, len(nums) - 1

    while left < right:
        mid = (left + right) // 2
        
        # Handle duplicates: when nums[mid] == nums[right], we can't decide the side
        if nums[mid] == nums[right]:
            right -= 1  # Shrink the right side, since we can't decide the side with duplicates
        elif nums[mid] > nums[right]:
            left = mid + 1  # min must be to the right of mid
        else:
            right = mid  # min is at mid or to the left of mid

    return nums[left]

```

*   **Time Complexity:** O(log n) — We keep halving the search space with each binary search step.

*   **Space Complexity:** O(1) — Only a few pointers (`left`, `right`, `mid`), no extra space used.
