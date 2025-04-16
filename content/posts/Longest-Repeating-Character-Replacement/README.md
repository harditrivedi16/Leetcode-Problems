---
id: 1757e332-de10-801a-93d0-df38f3b3fb73
title: Longest Repeating Character Replacement
created_time: 2025-01-08T18:03:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: >-
  https://leetcode.com/problems/longest-repeating-character-replacement/description/
my_confidence_level: Meduim
number: 45
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

Time Complexity: O(n)

Space Complexity: O(26)= O(1)
