---
id: 1317e332-de10-81e3-b080-e8469de5ef62
title: Product of Array Except Self
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-05-01T15:22:00.000Z
difficulty_level: 'Meduim '
remarks: |-
  Got the logic, 
  could also write code from logic
  logical errors in code
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Interview Questions
  - Blind 75
  - Neetcode - 150
problem_link: https://leetcode.com/problems/product-of-array-except-self/description/
my_confidence_level: High
last_solved: 2025-03-06T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked:
  - Amazon
  - Microsoft
  - Apple
  - Facebook/Meta
  - Bloomberg
  - Intuit
  - Adobe
  - Google
  - Uber
  - Yahoo
  - TicTok
problem_name: Product of Array Except Self

---

## Problem

## Solution

```python
class Solution: 
	def productExceptSelf(self, nums: List[int]) -> List[int]:
		res = [1] * len(nums)
		
		prefix = 1 
		for i in range(len(nums)): 
			res[i] = prefix 
			prefix *= nums[i]
		
		postfix = 1
		for i in range(len(nums) - 1, -1, -1): 
			res[i] *= postfix
			postfix *= nums[i]
			
		return res 
		
			
```

### Core Idea of the Solution

*   Initialize a result array `res` with 1s to store the final products.

*   Use a prefix product to store the product of all elements before each index.

*   Use a postfix product to multiply the product of all elements after each index.

### Why Use Prefix and Postfix

*   The prefix product accumulates the product of elements from the start up to each index, allowing the result array to hold the product of all preceding elements.

*   The postfix product accumulates the product of elements from the end back to each index, allowing the result array to be multiplied by the product of all succeeding elements.

*   Combining prefix and postfix products ensures that each index in the result array contains the product of all other elements except itself.

### Time Complexity and Space Complexity

*   **Time Complexity**: `O(N)`, where `N` is the number of elements in the input list, as we iterate through the list twice.

*   **Space Complexity**: `O(1)` for extra space, as the result array does not count towards extra space and only a few additional variables are used.
