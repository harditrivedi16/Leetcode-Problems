---
id: 1707e332-de10-807c-8cb8-fc46e5995599
title: Contains Duplicate II
created_time: 2025-01-03T19:05:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
difficulty_level: Easy
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/contains-duplicate-ii/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - Sliding Window
companies_asked:
  - Facebook/Meta
  - Google
  - Amazon
  - Microsoft
problem_name: Contains Duplicate II

---

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        start, end = 0 , 0
        window = set()
        

        while end < len(nums): 
            if nums[end] in window: 
                return True
            
            window.add(nums[end])

            if end - start + 1 > k: 
                window.remove(nums[start])
                start += 1
            end += 1 
        return False

        
```

Time complexity: O(n)

Space complexity: O(k)
