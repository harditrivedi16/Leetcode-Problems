---
id: 1317e332-de10-81fd-ac0d-e6c8432dd6c3
title: 'Search in rotated sorted array I '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:14:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Interview Questions
  - Neetcode - 150
problem_link: https://leetcode.com/problems/search-in-rotated-sorted-array/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Binary Search
  - Arrays
companies_asked:
  - Amazon
  - Google
  - Microsoft
  - Facebook/Meta
  - Apple
  - TicTok
  - Bloomberg
  - Grammarly
  - Walmart
problem_name: 'Search in rotated sorted array I '

---

```python
class Solution:

    def search(self, nums: List[int], target: int) -> int:
        def find_min_element(arr, N):
            start, end = 0, N - 1

            while start <= end:
                mid = (start + end) // 2
                prev = (mid + N - 1) % N
                nxt = (mid + 1) % N

                # Check if mid is the minimum element
                if arr[prev] >= arr[mid] <= arr[nxt]:
                    return mid
                # If mid to end is sorted, minimum is in the left part
                elif arr[mid] <= arr[end]:
                    end = mid - 1
                else:  # Minimum is in the right part
                    start = mid + 1

            return -1  # Should not reach here if the array is rotated

        def binary_search(arr, start, end, target):
            while start <= end:
                mid = (start + end) // 2
                if arr[mid] == target:
                    return mid
                elif arr[mid] < target:
                    start = mid + 1
                else:
                    end = mid - 1
            return -1

        N = len(nums)
        if N == 0:
            return -1

        # Step 1: Find the index of the smallest element
        min_index = find_min_element(nums, N)

        # Step 2: Perform binary search in the two halves
        left_result = binary_search(nums, 0, min_index - 1, target)
        right_result = binary_search(nums, min_index, N - 1, target)

        # Return the result from the side that found the target
        return left_result if left_result != -1 else right_result



        
```

*   **Time Complexity**: O(logN)

    O(log⁡N)

*   **Space Complexity**: O(1)

    O(1)
