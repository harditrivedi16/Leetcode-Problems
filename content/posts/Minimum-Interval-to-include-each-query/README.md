---
id: 1807e332-de10-80c2-9a9e-c676df68294b
title: Minimum Interval to include each query
created_time: 2025-01-19T18:07:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: >-
  https://leetcode.com/problems/minimum-interval-to-include-each-query/description/
my_confidence_level: Low
number: 58
last_solved: 2025-02-02T00:00:00.000Z
concept_involved:
  - Intervals
companies_asked:
  - Google
problem_name: Minimum Interval to include each query

---

```python
class Solution:
    def minInterval(self, intervals: List[List[int]], queries: List[int]) -> List[int]:
       intervals.sort()

       res, i, minHeap  = {}, 0, []

       for q in sorted(queries):

            while i < len(intervals) and intervals[i][0] <= q: 
                l, r = intervals[i]
                heapq.heappush(minHeap, (r-l + 1, r)) 
                i += 1
            
            while minHeap and minHeap[0][1] < q:
                heapq.heappop(minHeap)
            res[q] = minHeap[0][0] if minHeap else -1

       return [res[q] for q in queries]
```

Time Complexity: O(nlogn + qlogq)

Space Complexity:  O(n + 1)
