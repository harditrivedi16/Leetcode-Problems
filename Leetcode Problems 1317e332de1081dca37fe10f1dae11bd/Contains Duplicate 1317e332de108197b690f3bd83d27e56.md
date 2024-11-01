# Contains Duplicate

Companies asked : Adobe, Amazon, Apple, Bloomberg, Facebook/Meta, Google, Microsoft, Tcs, Uber, Yahoo
Concept involved: Arrays, Sets
Difficulty level: Easy
Last Solved : June 12, 2024
Leetcode Problem List: Blind 75, Neetcode - 150, Top Interview Questions
My Confidence Level : High
Number: 1
Problem Link: https://leetcode.com/problems/contains-duplicate/description/

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