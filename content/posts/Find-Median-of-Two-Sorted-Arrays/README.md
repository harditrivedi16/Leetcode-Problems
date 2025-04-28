---
id: 1e27e332-de10-806d-a092-c300343138f5
title: Find Median of Two Sorted Arrays
created_time: 2025-04-27T16:40:00.000Z
last_edited_time: 2025-04-27T16:54:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 148
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Find Median of Two Sorted Arrays

---

here say brute force would be to merge the sorted array and then find median, but we have a better sol.

```python
def findMedianSortedArrays(nums1, nums2):
    # Ensure nums1 is the smaller array
    if len(nums1) > len(nums2):
        nums1, nums2 = nums2, nums1
    
    m, n = len(nums1), len(nums2)
    left, right = 0, m
    
    while left <= right:
        partition1 = (left + right) // 2
        partition2 = (m + n + 1) // 2 - partition1
        
        # Handle edge cases for out-of-bound indices
        maxLeft1 = float('-inf') if partition1 == 0 else nums1[partition1 - 1]
        minRight1 = float('inf') if partition1 == m else nums1[partition1]
        
        maxLeft2 = float('-inf') if partition2 == 0 else nums2[partition2 - 1]
        minRight2 = float('inf') if partition2 == n else nums2[partition2]
        
        if maxLeft1 <= minRight2 and maxLeft2 <= minRight1:
            # Found correct partition
            if (m + n) % 2 == 0:
                return (max(maxLeft1, maxLeft2) + min(minRight1, minRight2)) / 2
            else:
                return max(maxLeft1, maxLeft2)
        elif maxLeft1 > minRight2:
            right = partition1 - 1
        else:
            left = partition1 + 1

```

*   The **median** is the middle value when combining two sorted arrays.

*   If the combined length of the arrays is odd, the median is the element in the middle.

*   If the combined length is even, the median is the average of the two middle elements.

We want to find the **median** using a more **efficient method** than just merging the arrays (which would be O(m + n)).
We can use **binary search** to reduce the problem to **O(log(min(m, n)))** complexity by focusing on the smaller array.

**How binary search works here:**

*   Perform binary search on the smaller of the two arrays.

*   Divide both arrays into two halves such that:

    *   The left half contains the smaller elements.

    *   The right half contains the larger elements.

*   Adjust the partitioning of both arrays to make sure that:

    *   The largest element on the left side is smaller than the smallest element on the right side.

*   If the condition is met, we can find the median:

    *   If combined length is odd, take the max of the left halves.

    *   If combined length is even, take the average of the max of the left halves and the min of the right halves.

Time Complexity:

**Complexity:**

*   **Time Complexity:** O(log(min(m, n))) — binary search on the smaller array.

*   **Space Complexity:** O(1) — no extra space used.
