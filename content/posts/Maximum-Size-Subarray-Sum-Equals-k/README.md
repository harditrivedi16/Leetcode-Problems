---
id: 1717e332-de10-80ab-97c1-e7871b19206e
title: Maximum Size Subarray Sum Equals k
created_time: 2025-01-04T02:36:00.000Z
last_edited_time: 2025-05-01T14:40:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Leetcode Curated Algorithms
problem_link: https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/
my_confidence_level: Low
last_solved: 2025-01-03T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked:
  - Facebook/Meta
problem_name: Maximum Size Subarray Sum Equals k

---

```python
class Solution:
    def maxSubArrayLen(self, nums: List[int], k: int) -> int:
        total = 0 
        result = 0 
        prefix_sum = {0: -1} 

        pointer = 0 

        while pointer < len(nums): 
            total += nums[pointer]

            if total - k in prefix_sum: 
                result = max(result, pointer - prefix_sum[total - k])

            if total not in prefix_sum: 
                prefix_sum[total] = pointer
            pointer += 1
        return result
        
```

Time complexity= O(n)

Space COmplexity = O(n)
