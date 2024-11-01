# Longest Consecutive Subsequence

Companies asked : Amazon, Bloomberg, Google, Infosys, Lyft, Meta, Microsoft, Oracle, TicTok, Zepto
Concept involved: Arrays, Sets
Difficulty level: Meduim 
Last Solved : October 3, 2024
Leetcode Problem List: Neetcode - 150, Top 100 Liked Questions, Top Interview Questions
My Confidence Level : Low
Number: 14
Problem Link: https://leetcode.com/problems/longest-consecutive-sequence/description/

### Longest Consecutive Subsequence

Given an unsorted array of integers `nums`, return *the length of the longest consecutive elements sequence.*

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

```
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is[1, 2, 3, 4]. Therefore its length is 4.

```

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
       # take advantage of O(1) lookup in hashset
       numsSet = set(nums)
       longest = 0 

       for n in nums: 
        if (n - 1) not in numsSet:
            length = 0 
            while (n + length) in numsSet: 
                length +=1 
                longest = max(length, longest)
       return longest

        
        
```

It iterates through each number, and if it identifies the start of a sequence (when `n - 1` is not present), it counts the length of that sequence by checking for subsequent numbers in the set.

- **Time Complexity**: O(n), where n is the number of elements in `nums`, since each element is processed once.
- **Space Complexity**: O(n) for storing the elements in the hash set.