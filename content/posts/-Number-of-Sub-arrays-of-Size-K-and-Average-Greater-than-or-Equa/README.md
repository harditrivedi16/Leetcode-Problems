---
id: 1707e332-de10-8016-859c-df2bd463866a
title: "\_Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold"
created_time: 2025-01-03T18:53:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/
my_confidence_level: High
number: 41
last_solved: 2025-01-03T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked:
  - Amazon
  - Linkedin
problem_name: "\_Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold"

---

```python
class Solution:
    def numOfSubarrays(self, arr: List[int], k: int, threshold: int) -> int:

        count = 0 
        start , end = 0, 0 
        total = 0 
        

        while end < len(arr): 
            total += arr[end]

            if end - start + 1 < k: 
                end += 1
            
            elif end - start + 1 == k: 
                if total >= threshold * k: 
                    count += 1 
                
                total -= arr[start]
                start += 1
                end += 1
        return count


        
```

Time Complexity: O(n)

Space Complexity: O(1)
