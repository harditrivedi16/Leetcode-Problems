---
id: 2787e332-de10-8033-a94a-fea8b17b1511
title: Remove Element
created_time: 2025-09-24T14:57:00.000Z
last_edited_time: 2025-09-24T15:07:00.000Z
difficulty_level: Easy
number: 19
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/remove-element/description/
my_confidence_level: Meduim
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked:
  - Google
  - Amazon
  - Microsoft
  - Facebook/Meta
  - Bloomberg
problem_name: Remove Element

---

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm). The order of the elements may be changed. Then return *the number of elements in* `nums` *which are not equal to* `val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

*   Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.

*   Return `k`.

Use two pointers to overwrite elements in `nums` directly:

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        k = 0  # write pointer

        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1

        return k


```

***

### 🧩 Explanation

*   Iterate through `nums`.

*   Whenever an element is not `val`, copy it to the position at index `k`.

*   Increment `k`.

*   After the loop, the first `k` elements of `nums` are the “cleaned” array.

***

### ⏱ Complexity

*   **Time:** O(n) (single pass)

*   **Space:** O(1) (in-place)
