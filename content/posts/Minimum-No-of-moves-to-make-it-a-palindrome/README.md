---
id: 1e27e332-de10-8001-bd4e-de27a516bf8a
title: Minimum No of moves to make it a palindrome
created_time: 2025-04-27T18:55:00.000Z
last_edited_time: 2025-05-01T15:34:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: 78
june_interviews_prep: null
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Two Pointers
companies_asked: []
problem_name: Minimum No of moves to make it a palindrome

---

```python
class Solution:
    def minMovesToMakePalindrome(self, s: str) -> int:
        s = list(s)

        res = 0 

        while s: 
            i = s.index(s[-1])

            if i == len(s) - 1: 
                res += (i// 2)
            else: 
                res += i 
                s.pop(i)
            s.pop()
        return res    
            

        
```

This solution uses a two-pointer-like approach, but it actually manipulates the string using the `list()` representation, which allows us to remove characters with `pop()` efficiently.

*   **Convert String to List**:
    The string `s` is converted into a list `s = list(s)` to allow easier manipulation (as strings are immutable in Python, we use a list to modify the string).

*   **Loop Until the List is Empty**:

    *   `while s:` continues the loop until the list `s` becomes empty.

*   **Find Matching Character**:

    *   `i = s.index(s[-1])` finds the first occurrence of the character at the end of the list (`s[-1]`). This is because we are trying to match the last character of the list to any previous occurrence.

*   **Check for Palindrome Character Pair**:

    *   If `i == len(s) - 1`, it means the character at the end is not paired with any earlier character. In this case, we are essentially "removing" the last character without finding a pair. So we calculate how many moves are needed to make the remaining string a palindrome by counting the number of shifts, which is `i // 2` (this is an approximation, but it works for the string's structure). Add this to the result `res`.

*   **Pairing and Removing Characters**:

    *   If `i != len(s) - 1`, it means we've found a matching character earlier in the list (at index `i`). We perform two operations:

        *   Add the number of moves needed to remove the character at `i` (which is just `i`).

        *   Use `s.pop(i)` to remove the character at index `i`.

*   **Remove the Last Character**:

    *   After handling the matching case or finding a non-pair at the end, we always remove the character at the end of the list using `s.pop()`.

*   **Return the Result**:

    *   After the loop finishes, the total number of moves required to make the string a palindrome is returned by `return res`.

### Time Complexity:

*   **Finding Index**: `s.index(s[-1])` takes O(n) in the worst case since it scans the entire list to find the last character.

*   **Looping**: We repeat the process while reducing the size of the list by removing elements, which involves removing one character at a time and repeating the `index` search.

    *   In total, the index search is called `n` times and on each iteration, the list size decreases by one.

*   **Overall Complexity**: The overall time complexity is **O(n^2)** because for each of the `n` characters, we are finding the index of the last character (which can take O(n) time) and then removing a character, which takes O(1) time.

### Space Complexity:

*   **List Storage**: The list `s` stores the characters of the string, so the space complexity is **O(n)** where `n` is the length of the string.

*   **Auxiliary Space**: Only a constant amount of extra space is used in terms of variables (`res`, `i`). So, the auxiliary space is **O(1)**.

### Summary:

*   **Time Complexity**: O(n^2)

*   **Space Complexity**: O(n)
