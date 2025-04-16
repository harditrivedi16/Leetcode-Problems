---
id: 14f7e332-de10-8088-9855-cc0bbaef6e95
title: Longest Substring without repeating characters
created_time: 2024-12-01T18:11:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
  - Top Interview Questions
problem_link: https://leetcode.com/problems/longest-substring-without-repeating-characters/
my_confidence_level: Meduim
number: 44
last_solved: 2025-01-08T00:00:00.000Z
concept_involved:
  - Sliding Window
  - Strings
companies_asked:
  - Google
  - Amazon
  - Microsoft
  - Bloomberg
  - Facebook/Meta
  - TicTok
  - IBM
  - Goldman Sachs
problem_name: Longest Substring without repeating characters

---

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        frequency_map = {}
        result = 0 
        start, end = 0,0 

        while end < len(s): 
            frequency_map[s[end]] = frequency_map.get(s[end], 0) + 1

            if frequency_map[s[end]] == 1: 
                result = max(result, end - start + 1)

            while frequency_map[s[end]] > 1: 
                frequency_map[s[start]] -= 1
                if frequency_map[s[start]] == 0: 
                    del frequency_map[s[start]]
                start += 1
            end += 1
        return result
        
```

Time Complexity = O(n)

Space Complexity = O(n)
