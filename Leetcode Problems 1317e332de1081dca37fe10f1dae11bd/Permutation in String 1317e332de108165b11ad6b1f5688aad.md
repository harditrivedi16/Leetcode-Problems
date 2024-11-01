# Permutation in String

Companies asked : Amazon, Facebook/Meta, Google, Microsoft, Oracle, TicTok, Yandex
Concept involved: Sliding Window, Strings
Difficulty level: Meduim 
Last Solved : October 22, 2024
Leetcode Problem List: Neetcode - 150, Top 100 Liked Questions
My Confidence Level : Low
Number: 22
Problem Link: https://leetcode.com/problems/permutation-in-string/

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

**Time Complexity**: \(O(n)\), where \(n\) is the length of `s2`, as we scan each character once.

**Space Complexity**: \(O(1)\), since the counters only store a fixed number of characters (at most 26 for lowercase English letters).