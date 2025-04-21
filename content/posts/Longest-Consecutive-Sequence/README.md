---
id: 1db7e332-de10-80b1-92d6-c527fbd87d22
title: Longest Consecutive Sequence
created_time: 2025-04-20T01:59:00.000Z
last_edited_time: 2025-04-20T15:41:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/longest-consecutive-sequence/
my_confidence_level: High
number: 92
last_solved: 2025-04-20T00:00:00.000Z
concept_involved:
  - Arrays
  - HashSet
companies_asked: []
problem_name: Longest Consecutive Sequence

---

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
       # take advantage of O(1) lookup in hashset
       numsSet = set(nums)
       longest = 0 

       for n in numsSet: 
        if (n - 1) not in numsSet:
            curr_num = n 
            curr_streak = 1 
            while curr_num + 1 in numsSet: 
                curr_streak += 1
                curr_num += 1 
            longest = max(curr_streak, longest)
       return longest
```

Time Complexity: O(n)

Space complexity: O(n)
