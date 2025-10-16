---
id: 1907e332-de10-8081-a2df-fea6a6cbc0ee
title: Check if One String Swap can make String Equal
created_time: 2025-02-04T16:55:00.000Z
last_edited_time: 2025-10-15T18:10:00.000Z
difficulty_level: Easy
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Strings
companies_asked:
  - Microsoft
  - Google
  - Amazon
problem_name: Check if One String Swap can make String Equal

---

```python
class Solution:
    def areAlmostEqual(self, s1: str, s2: str) -> bool:
        if s1 == s2: 
            return True 
        else: 
            diff = [[i,s1[i],s2[i]] for i in range(len(s1)) if s1[i]!= s2[i]]

        return len(diff) == 2 and diff[0][1] == diff[1][2] and diff[0][2] == diff[1][1]      
```

Time Comp = O(n)

Space Comp=O(n)
