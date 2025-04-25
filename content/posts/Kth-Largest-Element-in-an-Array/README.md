---
id: 14d7e332-de10-8064-b0a9-d975bbd0932b
title: Kth Largest Element in an Array
created_time: 2024-11-29T17:50:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Facebook Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/kth-largest-element-in-an-array/description/
my_confidence_level: High
number: 35
amazon_prep: 'No'
last_solved: 2025-04-14T00:00:00.000Z
concept_involved:
  - heaps
companies_asked:
  - Facebook/Meta
  - Amazon
  - Google
  - Microsoft
  - Linkedin
  - Oracle
  - ServiceNow
problem_name: Kth Largest Element in an Array

---

```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        #Logic of doing this is very similar
        #Here we will sort the list and iterate it from the back 
        minheap = []

        for num in nums: 
            heapq.heappush(minheap, num)

            if len(minheap) > k: 
                heapq.heappop(minheap)
        return minheap[0]

        #Kind of better solution
```

Time Complexity: O(nlogk)

Space Complexity: O(k)
