# Next Greater Element I

Companies asked : Amazon, Google, Microsoft, Oracle
Concept involved: Arrays, HashTables, Stack
Difficulty level: Easy
Last Solved : October 11, 2024
My Confidence Level : Meduim
Number: 19
Problem Link: https://leetcode.com/problems/next-greater-element-i/description/

```python
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        stack = []
        ngr = {}
        res = []

        # Traverse nums2 from right to left
        for i in range(len(nums2)-1, -1, -1):
            while stack and stack[-1] <= nums2[i]:
                stack.pop()
            if not stack:
                ngr[nums2[i]] = -1
            else:
                ngr[nums2[i]] = stack[-1]
            stack.append(nums2[i])

        # Now, for each element in nums1, find the next greater element
        for i in range(len(nums1)):
            res.append(ngr[nums1[i]])

        return res
```

1. The code builds a map (`ngr`) for each element in `nums2` to store the next greater element on its right using a stack to keep track of potential candidates in decreasing order.
2. Then, for each element in `nums1`, it looks up the precomputed next greater element from the `ngr` dictionary and adds it to the result list.

**Time Complexity**: O(n + m), where n is the size of `nums1` and m is the size of `nums2`.

**Space Complexity**: O(m) for the dictionary `ngr` and stack.