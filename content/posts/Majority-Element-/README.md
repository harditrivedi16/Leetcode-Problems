---
id: 1317e332-de10-8133-a4b2-f9baa815dc04
title: 'Majority Element '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:03:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/majority-element/description/
my_confidence_level: High
number: 10
last_solved: 2024-12-01T00:00:00.000Z
concept_involved:
  - Arrays
  - HashTables
companies_asked:
  - Amazon
  - Google
  - Bloomberg
  - Apple
  - Tcs
  - Adobe
  - Microsoft
  - Facebook/Meta
  - Nvidia
  - pwc
problem_name: 'Majority Element '

---

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

*   **collections.Counter:** This is used to count the frequency of each element in the array.

*   **Iterate through hashmap:** The loop iterates through each item in the hashmap. If the count of an element is more than `len(A)/2`, it immediately returns that element.

The time complexity is O(N) due to the single pass for counting elements and another for checking the majority, and the space complexity is O(N) in the worst case if all elements are unique.
