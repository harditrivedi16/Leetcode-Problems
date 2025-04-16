---
id: 1317e332-de10-8197-b690-f3bd83d27e56
title: 'Contains Duplicate '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:03:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top Interview Questions
  - Blind 75
problem_link: https://leetcode.com/problems/contains-duplicate/description/
my_confidence_level: High
number: 1
last_solved: 2024-11-20T00:00:00.000Z
concept_involved:
  - Arrays
  - Sets
companies_asked:
  - Amazon
  - Apple
  - Google
  - Uber
  - Microsoft
  - Bloomberg
  - Yahoo
  - Facebook/Meta
  - Adobe
  - Tcs
problem_name: 'Contains Duplicate '

---

## Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

### Sets Approach

Python also allows a data structure called set, which can also be useful in this scenario

```python
class Solution: 
	def containsDuplicate( self, nums: List[int])-> bool: 
		return True if len(set(nums)) < len(nums) else False )
	
```

**Time Complexity: O(n)** - The primary operation is the conversion of the list **`nums`** into a set. This operation traverses through each element in the list once to build the set, checking each element for uniqueness as it's added

**Space Complexity: O(n)** - The space complexity is also linear, as in the worst case (when there are no duplicates), a set containing all the elements of the list **`nums`** is created. T

### Hashtable Approach

Code:

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
         seen = {}  # This will act as our HashTable
         for num in nums:
            if num in seen: return True  # Duplicate found
            else: seen[num] = True
         return False
```

**Explanation:** This solution uses a dictionary to keep track of elements already seen. If an element is found in the dictionary, it indicates a duplicate, and the function returns **`True`**; otherwise, it adds the element to the dictionary and continues checking.

**Time Complexity: O(n)** - Each check (**`if num in seen`**) and insertion (**`seen[num] = True`**) operation in a dictionary (hash table) is, on average, O(1). Therefore, for **`n`** elements in the list, the overall average time complexity of the function is O(n).

**Space Complexity: O(n)** - In the worst case (when all elements are unique), the space complexity is proportional to the number of elements in **`nums`** because each element will be stored as a key in the dictionary **`seen`**. Thus, the space used grows linearly with the input size **`n`**.
