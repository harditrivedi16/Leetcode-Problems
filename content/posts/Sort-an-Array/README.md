---
id: 2787e332-de10-8084-84d0-d7e71aa82a3f
title: Sort an Array
created_time: 2025-09-24T15:22:00.000Z
last_edited_time: 2025-09-24T15:34:00.000Z
difficulty_level: 'Meduim '
number: 23
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/sort-an-array/description/
my_confidence_level: Meduim
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - Arrays
  - Sorting
companies_asked:
  - Google
  - Bloomberg
problem_name: Sort an Array

---

# 📊 Sorting Algorithms – Interview Cheat Sheet

Algorithm|Time Complexity (Best / Avg / Worst)|Space Complexity|Notes for Interview
\---|---|---|---
**QuickSort**|O(n log n) / O(n log n) / O(n²)|O(log n) (recursion)|In-place, very fast in practice, but worst case O(n²). Randomized pivot fixes most issues.
**MergeSort**|O(n log n) / O(n log n) / O(n log n)|O(n)|Stable, guaranteed O(n log n), but not in-place. Often used in external sorting.
**HeapSort**|O(n log n) / O(n log n) / O(n log n)|O(1)|In-place, guaranteed O(n log n), not stable, slightly slower than QuickSort in practice.
**InsertionSort**|O(n) / O(n²) / O(n²)|O(1)|Best for nearly sorted arrays or very small inputs.
**SelectionSort**|O(n²) / O(n²) / O(n²)|O(1)|Easy to understand, but inefficient. Rarely used.
**BubbleSort**|O(n) / O(n²) / O(n²)|O(1)|Only useful for teaching; never used in production.
**CountingSort**|O(n + k)|O(k)|Non-comparison sort, works only for integers in small range \[0..k]. Stable.
**RadixSort**|O(nk)|O(n + k)|Works for integers/strings with digits, stable.
**BucketSort**|O(n + k) (avg) / O(n²) (worst)|O(n + k)|Assumes uniform distribution; often combined with InsertionSort inside buckets.

***

# 🔹 Algorithms Explained

***

## 1. QuickSort

**Intuition:**

*   Pick a pivot.

*   Partition array so left < pivot, right ≥ pivot.

*   Recursively sort left and right.

**Code:**

```python
class Solution:
    def sortArray(self, nums):
        self.quickSort(nums, 0, len(nums)-1)
        return nums

    def quickSort(self, arr, low, high):
        if low < high:
            p = self.partition(arr, low, high)
            self.quickSort(arr, low, p-1)
            self.quickSort(arr, p+1, high)

    def partition(self, arr, low, high):
        pivot = arr[high]
        i = low - 1
        for j in range(low, high):
            if arr[j] <= pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]
        arr[i+1], arr[high] = arr[high], arr[i+1]
        return i+1


```

**Complexity:**

*   Time: O(n log n) avg, O(n²) worst (bad pivots).

*   Space: O(log n) recursion.

***

## 2. MergeSort

**Intuition:**

*   Divide into halves.

*   Recursively sort each half.

*   Merge two sorted halves.

**Code:**

```python
class Solution:
    def sortArray(self, nums):
        if len(nums) <= 1:
            return nums
        mid = len(nums) // 2
        left = self.sortArray(nums[:mid])
        right = self.sortArray(nums[mid:])
        return self.merge(left, right)

    def merge(self, left, right):
        merged, i, j = [], 0, 0
        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
                merged.append(left[i]); i += 1
            else:
                merged.append(right[j]); j += 1
        merged.extend(left[i:])
        merged.extend(right[j:])
        return merged


```

**Complexity:**

*   Time: O(n log n) always.

*   Space: O(n).

***

## 3. HeapSort

**Intuition:**

*   Convert array into a max-heap.

*   Repeatedly extract the max element, place at the end, shrink heap.

**Code:**

```python
class Solution:
    def sortArray(self, nums):
        n = len(nums)

        def heapify(n, i):
            largest = i
            l, r = 2*i+1, 2*i+2
            if l < n and nums[l] > nums[largest]:
                largest = l
            if r < n and nums[r] > nums[largest]:
                largest = r
            if largest != i:
                nums[i], nums[largest] = nums[largest], nums[i]
                heapify(n, largest)

        # build max-heap
        for i in range(n//2-1, -1, -1):
            heapify(n, i)

        # extract elements
        for i in range(n-1, 0, -1):
            nums[0], nums[i] = nums[i], nums[0]
            heapify(i, 0)

        return nums


```

**Complexity:**

*   Time: O(n log n).

*   Space: O(1).

***

## 4. Insertion Sort

**Intuition:**

*   Grow a sorted prefix.

*   Insert each new element in correct place.

**Code:**

```python
def insertionSort(nums):
    for i in range(1, len(nums)):
        key = nums[i]
        j = i-1
        while j >= 0 and nums[j] > key:
            nums[j+1] = nums[j]
            j -= 1
        nums[j+1] = key
    return nums


```

**Complexity:**

*   Time: O(n²), best case O(n) (nearly sorted).

*   Space: O(1).

***

## 5. Selection Sort

**Intuition:**

*   Find min element, put it at front.

*   Repeat for all positions.

**Code:**

```python
def selectionSort(nums):
    n = len(nums)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if nums[j] < nums[min_idx]:
                min_idx = j
        nums[i], nums[min_idx] = nums[min_idx], nums[i]
    return nums


```

**Complexity:**

*   Time: O(n²).

*   Space: O(1).

***

## 6. Bubble Sort

**Intuition:**

*   Repeatedly swap adjacent elements until sorted.

**Code:**

```python
def bubbleSort(nums):
    n = len(nums)
    for i in range(n):
        swapped = False
        for j in range(0, n-i-1):
            if nums[j] > nums[j+1]:
                nums[j], nums[j+1] = nums[j+1], nums[j]
                swapped = True
        if not swapped:
            break
    return nums


```

**Complexity:**

*   Time: O(n²), best case O(n).

*   Space: O(1).

***

## 7. Counting Sort

**Intuition:**

*   Count frequency of each number.

*   Rebuild sorted array.

*   Works only if numbers fall in a known, small range.

**Code:**

```python
def countingSort(nums):
    mn, mx = min(nums), max(nums)
    count = [0] * (mx - mn + 1)
    for num in nums:
        count[num - mn] += 1
    res = []
    for i, c in enumerate(count):
        res.extend([i+mn] * c)
    return res


```

**Complexity:**

*   Time: O(n + k).

*   Space: O(k).

*   k = range of numbers.
