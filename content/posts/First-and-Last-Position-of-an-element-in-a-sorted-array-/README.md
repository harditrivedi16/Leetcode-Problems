---
id: 1e27e332-de10-80d1-8a6c-d59762bae5c4
title: First and Last Position of an element in a sorted array.
created_time: 2025-04-27T16:24:00.000Z
last_edited_time: 2025-04-29T21:15:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: High
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: First and Last Position of an element in a sorted array.

---

```python
def searchRange(nums, target):
    def findFirst(nums, target):
        left, right = 0, len(nums) - 1
        first = -1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                first = mid
                right = mid - 1  # keep looking to the left
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return first

    def findLast(nums, target):
        left, right = 0, len(nums) - 1
        last = -1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                last = mid
                left = mid + 1  # keep looking to the right
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return last

    return [findFirst(nums, target), findLast(nums, target)]

```

**Time Complexity:**

O(log n) — each binary search is O(log n), and we do two searches, still O(log n).

✅

**Space Complexity:**

O(1) — we only use a few pointers.
