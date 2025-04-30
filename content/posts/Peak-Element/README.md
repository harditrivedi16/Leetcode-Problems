---
id: 1e27e332-de10-80eb-8f58-f1d44203798e
title: Peak Element
created_time: 2025-04-27T17:29:00.000Z
last_edited_time: 2025-04-29T21:16:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Peak Element

---

```python
python
CopyEdit
def findPeakElement(nums):
    def binarySearch(start, end):
        mid = start + (end - start) // 2

        # Check if mid is a peak element
        if (mid == 0 or nums[mid] > nums[mid - 1]) and (mid == len(nums) - 1 or nums[mid] > nums[mid + 1]):
            return mid

        # If the left neighbor is greater, peak must be in the left half
        elif mid > 0 and nums[mid] < nums[mid - 1]:
            return binarySearch(start, mid - 1)

        # If the right neighbor is greater, peak must be in the right half
        else:
            return binarySearch(mid + 1, end)

    return binarySearch(0, len(nums) - 1)


```

### **Approach (Refined):**

*   **Base Condition:**

    If the current element at `mid` is greater than both its neighbors (`nums[mid] > nums[mid-1]` and `nums[mid] > nums[mid+1]`), then it's a peak element. Return its index.

*   **Left Side Check:**

    If `nums[mid] < nums[mid-1]`, then there must be a peak on the left side (since a larger element must exist on that side), so you recursively search the left half by adjusting the `end` to `mid - 1`.

*   **Right Side Check:**

    If `nums[mid] < nums[mid+1]`, then there must be a peak on the right side, so you recursively search the right half by adjusting the `start` to `mid + 1`.

*   **Edge Case:**

    For the boundary conditions (i.e., the first or last element), you handle it by checking only one neighbor.

### **Code Implementation:**

### **Explanation:**

*   **Base Case:**

    When `nums[mid]` is greater than both its neighbors, we return `mid` because it’s a peak element.

*   **Left Side Search:**

    If `nums[mid] < nums[mid - 1]`, we recursively search the left part of the array (`start` to `mid - 1`).

*   **Right Side Search:**

    If `nums[mid] < nums[mid + 1]`, we recursively search the right part of the array (`mid + 1` to `end`).

*   **Edge Cases:**

    If `mid` is the first or last element, it only needs to be compared with its existing neighbor.

### **Time Complexity:**

*   The algorithm performs a binary search, so the time complexity is **O(log n)**, where `n` is the length of the array.

### **Space Complexity:**

*   The space complexity is **O(log n)** due to the recursive stack space in binary search.
