---
id: 1447e332-de10-8002-8350-fc7fa6767cc0
title: Find the minimum in a rotated sorted array I
created_time: 2024-11-20T00:30:00.000Z
last_edited_time: 2025-09-23T14:40:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
problem_link: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/
my_confidence_level: Meduim
last_solved: 2024-11-19T00:00:00.000Z
concept_involved:
  - Binary Search
  - Arrays
companies_asked:
  - Amazon
  - Facebook/Meta
  - TicTok
  - Microsoft
  - Apple
  - Google
problem_name: Find the minimum in a rotated sorted array I

---

```python
    def findMin(self, nums: List[int]) -> int:
            start, end = 0, len(nums) - 1
            N = len(nums)

            while start <= end:
                mid = (start + end) // 2
                prev = (mid + N - 1) % N  # Circular indexing for previous element
                next = (mid + 1) % N  # Circular indexing for next element
                
                # Check if the mid element is the minimum
                if nums[prev] >= nums[mid] <= nums[next]:
                    return nums[mid]
                
                # Determine which side to search based on the sorted portion
                if nums[mid] <= nums[end]:  # Right half is sorted, move left
                    end = mid - 1
                else:  # Left half is sorted, move right
                    start = mid + 1
            
            return -1  # Should not reach here if input is valid
```

Time complexity: O(logn)

Space Complexity: O(1)
