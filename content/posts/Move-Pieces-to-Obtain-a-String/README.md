---
id: 1547e332-de10-8054-a4db-e89b3c3280e5
title: Move Pieces to Obtain a String
created_time: 2024-12-06T00:13:00.000Z
last_edited_time: 2025-05-01T15:22:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/move-pieces-to-obtain-a-string/description/?envType=daily-question&envId=2024-12-05
my_confidence_level: Low
last_solved: 2024-12-05T00:00:00.000Z
concept_involved:
  - Strings
  - Two Pointers
companies_asked:
  - Google
  - Amazon
problem_name: Move Pieces to Obtain a String

---

```javascript
class Solution:
    def canChange(self, start: str, target: str) -> bool:
        
        def process(string): 
            return ''.join(c for c in string if c != '_')
        
       

        if process(start) != process(target): 
            return False

        i , j = 0,0
        n = len(start)

        while i < n and j < n: 
            while i < n and start[i] == '_': 
                i+= 1
            while j<n and target[j] == '_': 
                j += 1
            
            if i ==n or j ==n: 
                return i == j 
            
            if start[i] != target[j] or \
               (start[i] == 'L' and i < j) or \
               (start[i] == 'R' and i > j):


               return False

            i += 1 
            j += 1
        return True
```

Time Complexity: O(n)

Space Complexity: O(1)
