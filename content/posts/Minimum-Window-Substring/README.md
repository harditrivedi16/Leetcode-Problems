---
id: 1757e332-de10-80cb-80b4-d04f5a64cef0
title: Minimum Window Substring
created_time: 2025-01-08T18:03:00.000Z
last_edited_time: 2025-05-01T14:40:00.000Z
difficulty_level: Hard
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Interview Questions
  - Top Microsoft Questions
problem_link: https://leetcode.com/problems/minimum-window-substring/description/
my_confidence_level: Meduim
last_solved: 2025-01-08T00:00:00.000Z
concept_involved:
  - Sliding Window
  - Strings
companies_asked:
  - Facebook/Meta
  - Amazon
  - Google
  - TicTok
  - Microsoft
  - Lyft
problem_name: Minimum Window Substring

---

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        if not s or not t: 
            return "" 
        
        frequencyMap = collections.Counter(t)
        count = len(frequencyMap)
        minLength = float('inf')
        minStart = 0

        start, end = 0, 0 

        while end < len(s): 

            if s[end] in frequencyMap: 
                frequencyMap[s[end]] -= 1
                if frequencyMap[s[end]] == 0: 
                    count -= 1
            
            while count == 0: 

                windowSize = end - start + 1
                if windowSize < minLength: 
                    minLength = windowSize
                    minStart = start
                
                if s[start] in frequencyMap: 
                    frequencyMap[s[start]] += 1
                    if frequencyMap[s[start]] > 0: 
                        count +=1 

                start += 1
            

            end += 1
        return s[minStart : minStart + minLength] if minLength != float('inf') else ""


```

Problem Statement: **Minimum Window Substring**

**Problem:**

Given two strings `s` and `t`, find the smallest window in `s` that contains all the characters of `t`. If no such window exists, return an empty string.

logic for shrinking the window:

### `s[start]` **is in** `frequency_map`

*   We **increment** its count because we’re removing it from the window.

*   If this character **was already at 0**, then it was *just enough* to satisfy `t`. So removing it makes the window **invalid**, and we do `count += 1`.

*   This **stops shrinking** the window — we now need to move `end` again to make it valid.

### ✅ Case 2: `s[start]` **is not in** `frequency_map`

*   This character wasn't required in `t` at all.

*   So removing it doesn't affect the window's validity.

*   We can safely shrink the window to try to find a **smaller valid one**.

Time Complexity: O(s)

Space ComplexityO(no. of unique characters in t)
