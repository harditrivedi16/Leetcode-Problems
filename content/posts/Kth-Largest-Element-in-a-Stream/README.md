---
id: 14c7e332-de10-8071-b1bb-ca9d44d23290
title: Kth Largest Element in a Stream
created_time: 2024-11-28T22:10:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: Easy
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/kth-largest-element-in-a-stream/description/
my_confidence_level: Meduim
last_solved: null
concept_involved:
  - heaps
companies_asked:
  - Google
  - Facebook/Meta
problem_name: Kth Largest Element in a Stream

---

```python
import heapq
from typing import List

class KthLargest:
    def __init__(self, k: int, nums: List[int]):
        self.k = k
        self.minheap = []
        
        # Build the initial min-heap of size k
        for num in nums:
            heapq.heappush(self.minheap, num)
            if len(self.minheap) > k:
                heapq.heappop(self.minheap)

    def add(self, val: int) -> int:
        # Add the new value to the heap
        heapq.heappush(self.minheap, val)
        
        # Ensure the heap size remains at most k
        if len(self.minheap) > self.k:
            heapq.heappop(self.minheap)
        
        # The root of the heap is the kth largest element
        return self.minheap[0]

```

> 💡 A note on Python class, here we use self.*var\_name* only for those variable who are gonna be shared among multiple methods inside a class, for the variables who are gonna be shared only in one method and are temporary does require self.

Time Complexity: O(nlogk)

Space Complexity: k
