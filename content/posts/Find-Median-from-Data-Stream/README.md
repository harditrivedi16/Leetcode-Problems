---
id: 1d57e332-de10-80f2-b221-efc49630bcf1
title: Find Median from Data Stream
created_time: 2025-04-14T19:51:00.000Z
last_edited_time: 2025-04-24T16:50:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Top Interview Questions
  - Top Amazon Questions
  - Top Microsoft Questions
problem_link: https://leetcode.com/problems/find-median-from-data-stream/description/
my_confidence_level: Low
number: 76
amazon_prep: 'No'
last_solved: 2025-04-14T00:00:00.000Z
concept_involved:
  - Two Pointers
  - heaps
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
  - TicTok
  - Apple
  - Uber
problem_name: Find Median from Data Stream

---

```python
class MedianFinder:
    def __init__(self):
        # two heaps, large, small, minheap, maxheap
        # heaps should be equal size
        self.small, self.large = [], []  

    def addNum(self, num: int) -> None:
        if self.large and num > self.large[0]:
            heapq.heappush(self.large, num)
        else:
            heapq.heappush(self.small, -1 * num)

        if len(self.small) > len(self.large) + 1:
            val = -1 * heapq.heappop(self.small)
            heapq.heappush(self.large, val)
        if len(self.large) > len(self.small) + 1:
            val = heapq.heappop(self.large)
            heapq.heappush(self.small, -1 * val)

    def findMedian(self) -> float:
        if len(self.small) > len(self.large):
            return -1 * self.small[0]
        elif len(self.large) > len(self.small):
            return self.large[0]
        return (-1 * self.small[0] + self.large[0]) / 2.0
```

# **Time & Space Complexity**

**Time complexity: O(m∗log⁡n)*****O*****(*****m*****∗log*****n*****) for addNum()*****addNum*****(), O(m)*****O*****(*****m*****) for findMedian()*****findMedian*****().Space complexity: O(n)*****O*****(*****n*****)**

*   Time complexity: *O*(*m\_∗log\_n*) for *addNum*(), *O*(*m*) for *findMedian*().

    **O(m∗log⁡n)**

    **addNum()**

    **O(m)**

    **findMedian()**

*   Space complexity: *O*(*n*)

    **O(n)**

> Where mm is the number of function calls and nn is the length of the array.
