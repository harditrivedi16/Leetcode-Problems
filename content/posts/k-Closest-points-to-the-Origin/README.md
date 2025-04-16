---
id: 1d57e332-de10-8000-8073-fd64aa72941e
title: k Closest points to the Origin
created_time: 2025-04-14T17:53:00.000Z
last_edited_time: 2025-04-15T15:59:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top Amazon Questions
  - Top Facebook Questions
problem_link: https://leetcode.com/problems/k-closest-points-to-origin/description/
my_confidence_level: High
number: 73
last_solved: 2025-04-14T00:00:00.000Z
concept_involved:
  - heaps
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
problem_name: k Closest points to the Origin

---

```python
import heapq

class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        
        maxheap = []
        for point in points: 
            x, y = point[0], point[1]
            dist = -(x ** 2 + y ** 2)
            heapq.heappush(maxheap, (dist,(x,y)))
            if len(maxheap) > k: 
                heapq.heappop(maxheap)
        
        return [point for _ , point in maxheap]
            
```

Time Complexity: O(nlog(k))

Space Complexity: k
