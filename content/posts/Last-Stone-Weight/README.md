---
id: 1d57e332-de10-805e-90d1-d0cb6756b92d
title: Last Stone Weight
created_time: 2025-04-14T17:50:00.000Z
last_edited_time: 2025-04-15T15:59:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/last-stone-weight/
my_confidence_level: Meduim
number: 72
last_solved: 2025-04-14T00:00:00.000Z
concept_involved:
  - heaps
companies_asked:
  - Nvidia
  - Microsoft
  - Amazon
  - paypal
problem_name: Last Stone Weight

---

```python
import heapq

class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        stones = [-s for s in stones]
        heapq.heapify(stones) 

        while len(stones) >= 2: 
            first = -(heapq.heappop(stones))
            second = - (heapq.heappop(stones))
            if second != first:
                first = first - second
                heapq.heappush(stones,-first)
        
        return -stones[0] if stones else 0
```

Time Complexity: O(n(logn))

Space Complexity: O(n)
