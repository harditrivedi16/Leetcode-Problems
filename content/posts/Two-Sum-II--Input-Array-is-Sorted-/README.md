---
id: 1317e332-de10-8117-8607-c7019865baf3
title: 'Two Sum II: Input Array is Sorted '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-05-01T15:22:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
my_confidence_level: High
last_solved: 2025-03-20T00:00:00.000Z
concept_involved:
  - Arrays
  - Two Pointers
companies_asked:
  - Amazon
  - Facebook/Meta
  - Apple
  - Adobe
problem_name: 'Two Sum II: Input Array is Sorted '

---

## Two sum question with the array is sorted and asked the space complexity is constant

### Two Pointer Approach:

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:

        i, j = 0 , len(numbers) -1

        while i < j: 
            if numbers[j] + numbers[i] > target: 
                j -= 1 
            elif numbers[j] + numbers[i] < target: 
                i += 1
            else:
                return [i,j]
        return [-1, -1]
        
```

**Explanation:**

This **`twoSum`** function utilizes a two-pointer approach to find two numbers in a sorted array that add up to a given target. The pointers start at the beginning and end of the array, moving towards each other based on the sum comparison: if the sum is greater than the target, decrease the end pointer; if less, increase the start pointer. The function returns the indices of the two numbers that sum to the target, or **`[-1, -1]`** if no such pair exists.

**Time Complexity:** O(n), where n is the length of the array, since each element is checked at most once.

**Space Complexity:** O(1), as the solution uses only two pointers without additional storage.

with regards to leetcode question, it is an 1 indexed array so you need to return \[i+1, j+1 ]
