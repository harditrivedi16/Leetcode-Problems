---
id: 1bc7e332-de10-8070-a3e4-ddd31b9a2556
title: Longest Common Subsequence
created_time: 2025-03-20T16:25:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/longest-common-subsequence/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Dynamic Programming
companies_asked:
  - Google
  - Microsoft
  - Amazon
problem_name: Longest Common Subsequence

---

```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        n, m = len(text1), len(text2)

        t = [[-1] * (m+1) for _ in range(n+1)]

        for i in range(n+1): 
            for j in range(m+1): 
                if i == 0 or j == 0: 
                    t[i][j] = 0
        
        for i in range(1, n+1): 
            for j in range(1, m+1): 

                if text1[i-1] == text2[j-1]: 
                    t[i][j] = 1 + t[i-1][j-1]


                else: 
                    t[i][j] = max(t[i-1][j], t[i][j-1])
        

        return t[n][m]

        
```

Time Complexity: O(n\*m)

Space Complexity: O(n+1 \* m+1)
