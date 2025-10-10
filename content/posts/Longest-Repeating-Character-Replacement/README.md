---
id: 1757e332-de10-801a-93d0-df38f3b3fb73
title: Longest Repeating Character Replacement
created_time: 2025-01-08T18:03:00.000Z
last_edited_time: 2025-05-01T14:40:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: >-
  https://leetcode.com/problems/longest-repeating-character-replacement/description/
my_confidence_level: Meduim
last_solved: 2025-01-08T00:00:00.000Z
concept_involved:
  - Sliding Window
  - Strings
companies_asked:
  - Google
  - Bloomberg
  - Amazon
problem_name: Longest Repeating Character Replacement

---

```python
from collections import Counter
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        result = 0 
        frequencyMap = collections.Counter()
        start, end = 0, 0

        while end < len(s): 
            frequencyMap[s[end]] += 1 
            mostCommon = frequencyMap.most_common(1)[0][1]
            windowSize = end - start + 1
            if windowSize - mostCommon <= k: 
                result = max(result, windowSize)
            
            if windowSize - mostCommon > k: 
                
                frequencyMap[s[start]] -= 1
                if frequencyMap[s[start]] == 0: 
                    del frequencyMap[s[start]]
                start += 1

            end += 1
        return result
        


        
```

**Problem: Longest Repeating Character Replacement (LeetCode #424)**

You are given a string `s` and an integer `k`.

You can perform at most **k** character replacements in the string to make the longest substring with the same character.

Return the **length of the longest substring** that can be obtained by performing at most `k` replacements.

### Example:

```plain text
pgsql
CopyEdit
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'B's with 'A's, so the longest substring is "AAAA" wi

```

*   **`most_common(1)`**: This gets the most common element in `frequencyMap`. The number `1` indicates that we only want the **top 1** most frequent character.

*   `most_common(1)` returns a list of tuples, where each tuple is `(element, count)`—for example, `[('A', 5)]`.

*   **`[0][1]`**: This extracts the **count** of the most common element. In the example `('A', 5)`, `[0]` gets the first tuple, and `[1]` gets the count `5`.

Time Complexity: O(n)

Space Complexity: O(26)= O(1)
