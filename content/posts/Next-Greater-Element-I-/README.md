---
id: 1317e332-de10-8187-a76f-cd1b8e09f88b
title: 'Next Greater Element I '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/next-greater-element-i/description/
my_confidence_level: Meduim
number: 19
last_solved: 2024-10-11T00:00:00.000Z
concept_involved:
  - Stack
  - HashTables
  - Arrays
companies_asked:
  - Amazon
  - Google
  - Microsoft
  - Oracle
problem_name: 'Next Greater Element I '

---

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

*   The code builds a map (`ngr`) for each element in `nums2` to store the next greater element on its right using a stack to keep track of potential candidates in decreasing order.

*   Then, for each element in `nums1`, it looks up the precomputed next greater element from the `ngr` dictionary and adds it to the result list.

**Time Complexity**: O(n + m), where n is the size of `nums1` and m is the size of `nums2`.

**Space Complexity**: O(m) for the dictionary `ngr` and stack.
