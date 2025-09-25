---
id: 2787e332-de10-8086-858a-caf99b8bf6b7
title: Concatention of Array
created_time: 2025-09-24T14:32:00.000Z
last_edited_time: 2025-09-24T14:35:00.000Z
difficulty_level: Easy
number: 13
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/concatenation-of-array/description/
my_confidence_level: High
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked:
  - Google
problem_name: Concatention of Array

---

Given an integer array `nums` of length `n`, you want to create an array `ans` of length `2n` where `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n` (**0-indexed**).

Specifically, `ans` is the **concatenation** of two `nums` arrays.

Return *the array* `ans`.

```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        ans = nums + nums
        return ans
        
```

### Time Complexity

*   Concatenation (`nums + nums`) copies all elements of both lists into a new list.

*   If `n = len(nums)`, this takes **O(n)** time.

*   So, the **time complexity is O(n)**, not O(1).

***

### Space Complexity

*   A new list of size `2n` is created.

*   That means **O(n)** additional space.

*   So, the **space complexity is O(n)**, not O(1).
