---
id: 1447e332-de10-80fc-a360-d88882691130
title: 'Search in rotatedsorted array II '
created_time: 2024-11-20T00:33:00.000Z
last_edited_time: 2025-05-01T14:29:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/
my_confidence_level: Low
last_solved: 2024-11-19T00:00:00.000Z
concept_involved:
  - Binary Search
  - Arrays
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
  - Walmart
problem_name: 'Search in rotatedsorted array II '

---

```python
from typing import List

class Solution:
    def search(self, nums: List[int], target: int) -> bool:
        start, end = 0, len(nums) - 1

        while start <= end:
            mid = (start + end) // 2
            
            # Check if mid is the target
            if nums[mid] == target:
                return True
            
            # Handle duplicates
            if nums[start] == nums[mid] == nums[end]:
                start += 1
                end -= 1
            # If the left half is sorted
            elif nums[start] <= nums[mid]:
                if nums[start] <= target < nums[mid]:  # Target is in the left half
                    end = mid - 1
                else:  # Target is in the right half
                    start = mid + 1
            # If the right half is sorted
            else:
                if nums[mid] < target <= nums[end]:  # Target is in the right half
                    start = mid + 1
                else:  # Target is in the left half
                    end = mid - 1

        return False

```

Time complexity: O(logn)

Space Complexity: O(1)
