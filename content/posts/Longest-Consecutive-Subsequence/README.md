---
id: 1317e332-de10-8101-ba93-c795921fc3ca
title: Longest Consecutive Subsequence
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/longest-consecutive-sequence/description/
my_confidence_level: Low
last_solved: null
concept_involved:
  - Arrays
  - Sets
companies_asked:
  - Google
  - Amazon
  - Microsoft
  - Meta
  - Bloomberg
  - Oracle
  - Zepto
  - Infosys
  - TicTok
  - Lyft
problem_name: Longest Consecutive Subsequence

---

### Longest Consecutive Subsequence

Given an unsorted array of integers `nums`, return *the length of the longest consecutive elements sequence.*

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

```plain text
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

*   **Time Complexity**: O(n), where n is the number of elements in `nums`, since each element is processed once.

*   **Space Complexity**: O(n) for storing the elements in the hash set.
