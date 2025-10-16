---
id: 14f7e332-de10-809b-b895-e0e10b1c13ab
title: Range Addition
created_time: 2024-12-01T18:11:00.000Z
last_edited_time: 2025-10-15T18:10:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Leetcode Curated Algorithms
problem_link: https://leetcode.com/problems/range-addition/
my_confidence_level: Low
last_solved: null
concept_involved:
  - Arrays
companies_asked:
  - Google
problem_name: Range Addition

---

### Prefix - sum technique

```javascript
class Solution:
    def getModifiedArray(self, length: int, updates: List[List[int]]) -> List[int]:
        arr = [0] * (length + 1)
    
    # Apply the updates using difference array technique
        for start, end, inc in updates:
            arr[start] += inc  # Mark the start of increment
            if end + 1 < length:
                arr[end + 1] -= inc  # Mark the end of increment + 1
        
        # Compute the final array using prefix sum
        result = []
        current = 0
        for i in range(length):
            current += arr[i]
            result.append(current)
        
        return result
```
