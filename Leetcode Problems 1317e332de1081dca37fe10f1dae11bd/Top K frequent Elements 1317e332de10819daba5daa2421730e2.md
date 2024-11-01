# Top K frequent Elements

Companies asked : Adobe, Amazon, Apple, Avito, Bloomberg, Facebook/Meta, Google, Intuit, Microsoft, Netflix, Oracle, TicTok, Uber, Walmart, Yahoo, paypal
Concept involved: Arrays, HashTables, heaps
Difficulty level: Meduim 
Last Solved : July 8, 2024
Leetcode Problem List: Neetcode - 150, Top 100 Liked Questions, Top Facebook Questions, Top Interview Questions
My Confidence Level : Low
Number: 11
Problem Link: https://leetcode.com/problems/top-k-frequent-elements/

## Problem:

Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in **any order**.

**Example 1:**

```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
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

1. Use `Counter` to count the frequency of each element in the list.
2. Maintain a min-heap of size `k` to store the top `k` frequent elements.
3. Return the elements from the heap as the result.

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

1. Count the frequency of each element in the input list using a dictionary.
2. Use bucket sort to group elements by their frequency into a list of lists.
3. Iterate through the buckets in reverse order to collect the top K frequent elements.
4. Return the collected top K elements as the result.

### Explanation of Bucket Sort and Its Optimization

Bucket sort is used to group elements by their frequency, where each bucket at index `i` contains elements that appear `i` times. This approach optimizes the solution by avoiding the need to maintain a heap, which can be more complex and slower in practice. Instead of maintaining a min-heap of size K, bucket sort leverages the fact that the maximum possible frequency of any element is bounded by the length of the input list. This simplifies the process of finding the top K frequent elements by directly accessing the buckets in descending order of frequency.

### Time Complexity and Space Complexity

- **Time Complexity**: `O(N)`, where `N` is the number of elements in the input list.
- **Space Complexity**: `O(N)`, due to the space required for the frequency dictionary and the bucket list.