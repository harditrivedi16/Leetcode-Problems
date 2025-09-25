---
id: 2787e332-de10-808e-97b1-de4aa11b7cc4
title: Sort Colors
created_time: 2025-09-24T15:35:00.000Z
last_edited_time: 2025-09-24T15:47:00.000Z
difficulty_level: 'Meduim '
number: 24
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/sort-colors/description/
my_confidence_level: Meduim
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - Arrays
  - Sorting
companies_asked:
  - Google
  - Amazon
  - Facebook/Meta
  - Bloomberg
  - Morgan Stanley
  - Microsoft
  - Walmart
  - Visa
  - Tcs
  - Salesforce
problem_name: Sort Colors

---

Given an array `nums` with `n` objects colored red, white, or blue, sort them [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

## Dutch National Flag (Preferred)

**Intuition:**

*   Maintain three regions:

    *   `[0 … low-1]` → all 0s

    *   `[low … mid-1]` → all 1s

    *   `[high+1 … end]` → all 2s

*   Traverse with `mid`:

    *   If `nums[mid] == 0`: swap with `low`, expand both `low` and `mid`.

    *   If `nums[mid] == 1`: just move `mid`.

    *   If `nums[mid] == 2`: swap with `high`, shrink `high`.

**Code:**

```python
class Solution:
    def sortColors(self, nums):
        low, mid, high = 0, 0, len(nums) - 1

        while mid <= high:
            if nums[mid] == 0:
                nums[low], nums[mid] = nums[mid], nums[low]
                low += 1
                mid += 1
            elif nums[mid] == 1:
                mid += 1
            else:  # nums[mid] == 2
                nums[mid], nums[high] = nums[high], nums[mid]
                high -= 1


```

**Complexity:**

*   Time: O(n)

*   Space: O(1)

***

## ✅ Counting Sort (Alternative)

**Intuition:** Count how many 0s, 1s, and 2s, then overwrite.

```python
class Solution:
    def sortColors(self, nums):
        count0 = count1 = count2 = 0
        for num in nums:
            if num == 0: count0 += 1
            elif num == 1: count1 += 1
            else: count2 += 1

        nums[:] = [0]*count0 + [1]*count1 + [2]*count2


```

**Complexity:**

*   Time: O(n)

*   Space: O(1) (if you overwrite in place as shown).

***

👉 **Takeaway for interviews:**

*   **Dutch National Flag** is the expected answer (shows algorithmic thinking).

*   **Counting sort** is valid but too trivial — usually they’ll push you toward the 3-pointer solution.
