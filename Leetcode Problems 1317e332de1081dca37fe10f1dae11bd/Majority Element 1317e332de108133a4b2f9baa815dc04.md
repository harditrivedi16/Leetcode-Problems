# Majority Element

Companies asked : Adobe, Amazon, Apple, Bloomberg, Facebook/Meta, Google, Microsoft, Nvidia, Tcs, pwc
Concept involved: Arrays, HashTables
Difficulty level: Easy
Last Solved : June 17, 2024
Leetcode Problem List: Top 100 Liked Questions, Top Interview Questions
My Confidence Level : Meduim
Number: 10
Problem Link: https://leetcode.com/problems/majority-element/description/

Given an array `nums` of size `n`, return *the majority element*.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

```python
class Solution:
	def majorityElement(self, nums: List[int]) -> int:
		hashmap = collections.Counter(nums)
		for key, value in hashmap.items():
			if value > len(nums)/2:
				return key
```

### Explanation:

- **collections.Counter:** This is used to count the frequency of each element in the array.
- **Iterate through hashmap:** The loop iterates through each item in the hashmap. If the count of an element is more than `len(A)/2`, it immediately returns that element.

The time complexity is O(N) due to the single pass for counting elements and another for checking the majority, and the space complexity is O(N) in the worst case if all elements are unique.