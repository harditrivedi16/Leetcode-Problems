---
id: 1e27e332-de10-8060-8525-ed2b6afc23fe
title: Find the occurence of the First index of a string
created_time: 2025-04-27T19:15:00.000Z
last_edited_time: 2025-05-01T15:34:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 79
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Two Pointers
  - Strings
  - Sliding Window
companies_asked: []
problem_name: Find the occurence of the First index of a string

---

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        # If needle is empty, return 0 (as per problem statement)
        if not needle:
            return 0
        
        # Lengths of haystack and needle
        n, m = len(haystack), len(needle)
        
        # If needle is longer than haystack, return -1
        if m > n:
            return -1
        
        # Sliding window approach to compare substrings
        for i in range(n - m + 1):
            # Check if the substring matches the needle
            if haystack[i:i+m] == needle:
                return i
        
        return -1

```

### Problem Statement:

Given a string `haystack` and a string `needle`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

**Manual Sliding Window Approach**:

*   We can slide the `needle` across the `haystack` and check at each position whether the substring starting from that position matches the `needle`. This approach mimics how substring search algorithms work.

**Sliding Window Approach**:

*   **Time Complexity**: O(n \* m), where `n` is the length of `haystack` and `m` is the length of `needle`. In the worst case, for each position in `haystack`, we compare up to `m` characters (substring comparison).

*   **Space Complexity**: O(1), as we only use a few variables to store the indices and lengths. No additional space for strings or arrays is used.
