---
id: 1707e332-de10-8022-baf7-d41aae1b192e
title: Sliding Window Maximum
created_time: 2025-01-03T18:38:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Amazon Questions
  - Top Interview Questions
problem_link: https://leetcode.com/problems/sliding-window-maximum/
my_confidence_level: Low
number: 40
amazon_prep: 'No'
last_solved: 2025-01-03T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked:
  - Amazon
  - Facebook/Meta
  - Google
  - Apple
  - TicTok
  - Goldman Sachs
problem_name: Sliding Window Maximum

---

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:

        result = []

        dq = deque()

        start = 0 
        end = 0 

        while end < len(nums): 

            while dq and dq[-1] < nums[end]: 
                dq.pop()
            dq.append(nums[end])

            if end - start + 1 < k: 
                end += 1

            elif end - start + 1 == k : 
                result.append(dq[0])

                if dq and dq[0] == nums[start]: 
                    dq.popleft()
                start += 1
                end += 1
        return result
                

        
```

Time complexity: O(n)

space Complexity: O(k)
