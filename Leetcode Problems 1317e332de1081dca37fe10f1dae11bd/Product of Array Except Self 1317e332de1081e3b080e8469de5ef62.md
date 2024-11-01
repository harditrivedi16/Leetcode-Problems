# Product of Array Except Self

Companies asked : Adobe, Amazon, Apple, Bloomberg, Facebook/Meta, Google, Intuit, Microsoft, TicTok, Uber, Yahoo
Concept involved: Arrays
Difficulty level: Meduim 
Last Solved : October 3, 2024
Leetcode Problem List: Blind 75, Neetcode - 150, Top 100 Liked Questions, Top Interview Questions
My Confidence Level : Low
Number: 12
Problem Link: https://leetcode.com/problems/product-of-array-except-self/description/

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

1. Initialize a result array `res` with 1s to store the final products.
2. Use a prefix product to store the product of all elements before each index.
3. Use a postfix product to multiply the product of all elements after each index.

### Why Use Prefix and Postfix

1. The prefix product accumulates the product of elements from the start up to each index, allowing the result array to hold the product of all preceding elements.
2. The postfix product accumulates the product of elements from the end back to each index, allowing the result array to be multiplied by the product of all succeeding elements.
3. Combining prefix and postfix products ensures that each index in the result array contains the product of all other elements except itself.

### Time Complexity and Space Complexity

- **Time Complexity**: `O(N)`, where `N` is the number of elements in the input list, as we iterate through the list twice.
- **Space Complexity**: `O(1)` for extra space, as the result array does not count towards extra space and only a few additional variables are used.