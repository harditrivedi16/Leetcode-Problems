---
id: 1e27e332-de10-8026-ba8d-f28e8049596d
title: Find kth Smallest Pair Distance
created_time: 2025-04-27T17:04:00.000Z
last_edited_time: 2025-04-27T17:23:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 151
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Find kth Smallest Pair Distance

---

```python
def countPairs(nums, mid):
    count = 0
    left = 0
    for right in range(1, len(nums)):
        # Move the left pointer to ensure nums[right] - nums[left] <= mid
        while nums[right] - nums[left] > mid:
            left += 1
        # Count the number of valid pairs ending at 'right'
        count += (right - left)
    return count

def smallestDistancePair(nums, k):
    nums.sort()  # Sorting the array to calculate pair distances efficiently
    
    # Binary search over the possible distance values (from 0 to max distance)
    low, high = 0, nums[-1] - nums[0]
    while low < high:
        mid = (low + high) // 2
        if countPairs(nums, mid) < k:
            low = mid + 1
        else:
            high = mid
    return low

```

Bruteforce: calculate pairs, put it in a sorted order and then give the index of kth element. sorting and indexing can be optimized using min heap.

Approach:

Binary search on \[0,max(nums)]- find mid and calculate how many pairs have the have dist that is equal to or smaller than mid, and continue binary search.
we find the count using sliding window.

so it is more of like sliding window + binary search problem.

### **Time Complexity:**

*   **Sorting the Array**: Sorting the array takes `O(n log n)` where `n` is the length of the `nums` array.

*   **Binary Search**: We perform binary search over the possible pair distances, which takes `O(log(max(nums) - min(nums)))`. In the worst case, this can be `O(n)` since the pair distance range is at most `n`.

*   **Counting Pairs**: For each `mid` value in the binary search, the `countPairs` function runs in `O(n)` time as it iterates over the array with the two-pointer technique.

Thus, the overall time complexity is:

*   **O(n log n)** for sorting.

*   **O(n log(max(nums) - min(nums)))** for binary search and counting pairs.

**Total Time Complexity**:

**O(n log n + n log(max(nums) - min(nums)))**.

### **Space Complexity:**

*   **Space for Sorting**:

    The space complexity is `O(n)` for the sorted array.

*   **Auxiliary Space**:

    The `countPairs` function uses constant space (`O(1)`), and the binary search also requires constant space.

Thus, the overall space complexity is:

*   **O(n)** due to sorting.
