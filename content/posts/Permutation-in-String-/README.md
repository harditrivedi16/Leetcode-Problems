---
id: 1317e332-de10-8165-b11a-d6b1f5688aad
title: 'Permutation in String '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-05-01T15:22:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
problem_link: https://leetcode.com/problems/permutation-in-string/
my_confidence_level: Meduim
last_solved: 2025-01-03T00:00:00.000Z
concept_involved:
  - Strings
  - Sliding Window
companies_asked:
  - Google
  - Microsoft
  - Amazon
  - Yandex
  - Facebook/Meta
  - Oracle
  - TicTok
problem_name: 'Permutation in String '

---

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:

        # In case the ask the indices of the anagrams
        #res = []

        # check for edge conditions 
        if len(s1) > len(s2): 
            #return res 
            return False 

        #Initialize the sliding window pointers
        start = 0
        end = 0

        s1_count= Counter(s1)
        s2_count= Counter()

        while end < len(s2): 

            # calculations
            s2_count[s2[end]] += 1

            # Reach the window size
            if (end - start + 1 ) < len(s1): 
                end += 1 

            # Maintain the window size
            elif (end - start + 1) == len(s1): 

                # cal to result 
                if s2_count == s1_count: 
                    return True 
                    #res.append[s2[start]]
                    #res.append[s2[start:end+1]
                
                # slide the window
                s2_count[s2[start]] -= 1
                if s2_count[s2[start]] == 0: 
                    del s2_count[s2[start]]

                start += 1
                end += 1

        return False 
        #return result
```

The solution uses a **sliding window** approach to check if `s1`'s characters (with their frequencies) can be found as a contiguous substring in `s2`. It initializes frequency counters for `s1` and an empty counter for `s2`, which tracks the current window in `s2`. The window slides one character at a time, updating the counter and checking if the current window matches `s1`'s frequency. If a match is found, it returns `True`; otherwise, it continues sliding the window until the end of `s2`.

**Time Complexity**: (O(n)), where (n) is the length of `s2`, as we scan each character once.

**Space Complexity**: (O(1)), since the counters only store a fixed number of characters (at most 26 for lowercase English letters).
