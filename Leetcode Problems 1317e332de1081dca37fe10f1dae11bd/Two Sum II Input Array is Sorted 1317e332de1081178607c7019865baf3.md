# Two Sum II: Input Array is Sorted

Companies asked : Adobe, Amazon, Apple, Facebook/Meta
Concept involved: Arrays, Two Pointers
Difficulty level: Meduim 
Last Solved : October 14, 2024
Leetcode Problem List: Neetcode - 150
My Confidence Level : High
Number: 5
Problem Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/

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

with regards to leetcode question, it is an 1 indexed array so you need to return [i+1, j+1 ]