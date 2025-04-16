---
id: 1317e332-de10-819d-aba5-daa2421730e2
title: 'Top K frequent Elements '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: 'Meduim '
remarks: |-
  - got the logic in head, 
  - could not convert the logic into code
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Facebook Questions
  - Top Interview Questions
  - Neetcode - 150
problem_link: https://leetcode.com/problems/top-k-frequent-elements/
my_confidence_level: Meduim
number: 11
last_solved: 2025-03-06T00:00:00.000Z
concept_involved:
  - Arrays
  - HashTables
  - heaps
companies_asked:
  - Facebook/Meta
  - Amazon
  - Bloomberg
  - Apple
  - Oracle
  - Google
  - Microsoft
  - Adobe
  - Walmart
  - Netflix
  - Avito
  - Uber
  - Yahoo
  - Intuit
  - paypal
  - TicTok
problem_name: 'Top K frequent Elements '

---

## Problem:

Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in **any order**.

**Example 1:**

```plain text
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        # Step 1: Count frequency of elements using Counter
        count = collections.Counter(nums)
        
        # Step 2: Get the k most frequent elements
        ans = [item[0] for item in count.most_common(k)]
        
        return ans
        
```

## Heap Solution

### Solution Code

```python
import heapq
from collections import Counter

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        count = Counter(nums)
        heap = []

        for num, freq in count.items():
            heapq.heappush(heap, (freq, num))
            if len(heap) > k:
                heapq.heappop(heap)

        return [num for freq, num in heap]

```

### Core Idea in Three Lines

*   Use `Counter` to count the frequency of each element in the list.

*   Maintain a min-heap of size `k` to store the top `k` frequent elements.

*   Return the elements from the heap as the result.

### Explanation of Min-Heap and Its Use

A min-heap is a binary tree where the smallest element is at the root, ensuring that any parent node is less than or equal to its children. In this problem, we use a min-heap to efficiently keep track of the top `k` frequent elements. By maintaining a min-heap of size `k`, we ensure that we only store the `k` most frequent elements and discard any less frequent ones. Using a max-heap would require storing all elements and then extracting the top `k`, which is less efficient in terms of space (`O(N)` vs. `O(K)`) and time complexity for extraction (`O(K log N)` vs. `O(N log K)`).

### Time and Space Complexity

The time complexity is `O(N log K)` and the space complexity is `O(K)` for storing the heap.

## O(n) solution - Bucket Sort Approach.

### Solution Code:

```python
class Solution: 
	def topKFrequent(self, nums: List[int], k: int) -> List[int]: 
		count = {}
		freq = [[] for i in range(len(nums)+ 1)]
		
		for n in nums: 
			count [n] = 1 + count.get(n,0)
			for n,c in count.items():
				freq[c].append(n)
				
		res = []
		for in in range(len(freq) -1, 0, -1):
			for n in freq[i]: 
				res.append(n)
				if len(res) == k: 
				  return res
```

### Core Idea Behind the Algorithm

*   Count the frequency of each element in the input list using a dictionary.

*   Use bucket sort to group elements by their frequency into a list of lists.

*   Iterate through the buckets in reverse order to collect the top K frequent elements.

*   Return the collected top K elements as the result.

### Explanation of Bucket Sort and Its Optimization

Bucket sort is used to group elements by their frequency, where each bucket at index `i` contains elements that appear `i` times. This approach optimizes the solution by avoiding the need to maintain a heap, which can be more complex and slower in practice. Instead of maintaining a min-heap of size K, bucket sort leverages the fact that the maximum possible frequency of any element is bounded by the length of the input list. This simplifies the process of finding the top K frequent elements by directly accessing the buckets in descending order of frequency.

### Time Complexity and Space Complexity

*   **Time Complexity**: `O(N)`, where `N` is the number of elements in the input list.

*   **Space Complexity**: `O(N)`, due to the space required for the frequency dictionary and the bucket list.
