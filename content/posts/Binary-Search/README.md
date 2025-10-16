---
id: 1447e332-de10-80e5-a943-f93659678b87
title: Binary Search
created_time: 2024-11-20T00:49:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: Easy
remarks: |-
  remember: 
  (1) while start ≤ end and not start < end
  (2) mid = (start + end) // 2; // is for floor division
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
problem_link: https://leetcode.com/problems/binary-search/
my_confidence_level: High
last_solved: null
concept_involved:
  - Binary Search
  - Arrays
companies_asked:
  - Google
  - Bloomberg
  - Facebook/Meta
problem_name: Binary Search

---

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        s = 0
        e = len(nums)- 1
        
        while s <= e:
            mid = (s+e)//2

            if nums[mid] == target:
                return mid
            elif nums[mid] >= target:
                e = mid-1
            else:
                s = mid+1

        return -1 
        
```

Time Complexity: O(logn)

Space Complexity: O(1)
