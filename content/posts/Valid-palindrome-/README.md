---
id: 1317e332-de10-81a0-8bcf-f7ef5ca6762d
title: 'Valid palindrome '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
difficulty_level: Easy
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top Interview Questions
  - Neetcode - 150
  - Blind 75
  - Top Facebook Questions
problem_link: https://leetcode.com/problems/valid-palindrome/
my_confidence_level: High
last_solved: null
concept_involved:
  - Strings
  - Two Pointers
companies_asked:
  - Facebook/Meta
  - Yandex
  - Apple
  - Amazon
  - Adobe
  - TicTok
  - Google
problem_name: 'Valid palindrome '

---

## A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers. Given a string `s`, return `true` *if it is a* ***palindrome**\_\_, or* `false` *otherwise*.

### Two Pointer’s Approach

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:

        i , j = 0, len(s) - 1 

        while i < j: 
            while i < j and not s[i].isalnum():
                i += 1
            while i < j and not s[j].isalnum():
                j-=1
            
            if s[i].lower() != s[j].lower():
                return False 

            i += 1
            j -= 1

        
        return True 
```

So, if we start traversing inwards, from both ends of the input string, we can expect to *see* the same characters, in the same order.

The resulting algorithm is simple:

*   Set two pointers, one at each end of the input string

*   If the input is palindromic, both the pointers should point to equivalent characters, *at all times*.

    *   If this condition is not met at any point of time, we break and return early.

*   We can simply ignore non-alphanumeric characters by using isalnum() function continuing to traverse further.

*   Continue traversing inwards until the pointers meet in the middle.

*   **Time complexity** : O(n) in length *n* of the string. We traverse over each character at-most once, until the two pointers meet in the middle, or when we break and return early.

*   **Space complexity :** O(1). No extra space required, at all.
