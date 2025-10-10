---
id: 1447e332-de10-807a-9ca1-f09ce1ccc881
title: 'Find the minimum in the rotated sorted array II '
created_time: 2024-11-20T00:33:00.000Z
last_edited_time: 2025-05-01T14:29:00.000Z
difficulty_level: Hard
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/description/
my_confidence_level: Low
last_solved: 2024-11-19T00:00:00.000Z
concept_involved:
  - Binary Search
  - Arrays
companies_asked:
  - Google
problem_name: 'Find the minimum in the rotated sorted array II '

---

```python
from typing import List

class Solution:
    def findMin(self, nums: List[int]) -> int:
        start, end = 0, len(nums) - 1
        N = len(nums)

        while start <= end:
            mid = (start + end) // 2
            prev = (mid + N - 1) % N  # Circular indexing for previous element
            next = (mid + 1) % N  # Circular indexing for next element
            
            # Check if the mid element is the minimum
            if nums[mid] < nums[prev] and nums[mid] < nums[next]:
                return nums[mid]
            
            if nums[mid] < nums[end]:  # Right part is sorted, go left
                end = mid
            elif nums[mid] > nums[end]:  # Minimum is in the right part
                start = mid + 1
            else:  # nums[mid] == nums[end], reduce the search space conservatively
                end -= 1
        
        # Start will point to the minimum element
        return nums[start]
```

Time Complexity :O(logn)

Space Complexity: O(1)
