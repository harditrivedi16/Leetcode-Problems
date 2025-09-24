---
id: 1e17e332-de10-80b2-abb8-fba18f19b65b
title: 'Maximum No. of Books you can take '
created_time: 2025-04-26T16:24:00.000Z
last_edited_time: 2025-05-01T14:40:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked: []
problem_name: 'Maximum No. of Books you can take '

---

```python

def maxBooks(books, maxPages):
    n = len(books)
    # If the array has no books, return 0
    if n == 0:
        return 0

    # Use sliding window on the linear array
    def sliding_window(arr):
        left = 0
        current_sum = 0
        max_books = 0
        for right in range(len(arr)):
            current_sum += arr[right]
            while current_sum > maxPages:
                current_sum -= arr[left]
                left += 1
            max_books = max(max_books, right - left + 1)
        return max_books

    # First, calculate the max books in the linear array
    max_books_in_linear = sliding_window(books)

    # Now simulate the circular array by concatenating the array to itself
    # and apply sliding window again on the concatenated array
    max_books_in_circular = sliding_window(books + books)

    return min(max_books_in_circular, n)  # We can't select more than `n` books



```

### **Problem Statement:**

You are given an array `books` where each element represents the number of pages of a book. You are asked to find the maximum number of books you can take such that the sum of pages of the selected books does not exceed a given limit, `maxPages`.

The books are arranged in a circular manner, meaning you can pick books from any part of the array (starting from any index) and form a subarray. However, the sum of the pages of the books you pick cannot exceed `maxPages`.

**You need to return the maximum number of books you can select.**

### **Approach:**

This is a sliding window problem where we need to find the largest subarray (in a circular manner) whose sum does not exceed `maxPages`. The trick here is to handle the circular nature of the problem.

*   **Sliding Window (Linear Array):**

    *   Start by finding the largest subarray sum for a normal (non-circular) array.

    *   Use two pointers (left and right) to maintain the window.

    *   If the sum of the pages in the current window exceeds `maxPages`, increment the `left` pointer to shrink the window until the sum is valid again.

*   **Handling the Circular Nature:**

    *   After calculating the maximum sum for the linear array, simulate the circular array by concatenating the array to itself. This allows us to treat the problem as a normal subarray problem by using a sliding window on the concatenated array.

    *   The total number of books we can select is the maximum number of books that can be chosen without exceeding the page limit `maxPages`.

***

### **Code Implementation:**

### **Explanation:**

*   **Sliding Window:**

    *   We maintain a window `[left, right]` where `current_sum` is the sum of elements in this window.

    *   If `current_sum` exceeds `maxPages`, we increment `left` to reduce the window size and bring the sum within the allowed limit.

    *   For each valid window, we update `max_books` to track the maximum number of books that can be selected.

*   **Circular Array Simulation:**

    *   By concatenating the array (`books + books`), we can simulate the circular nature of the problem.

    *   We apply the same sliding window algorithm to this concatenated array, ensuring we don't select more than `n` books (because the maximum possible number of books in any subarray is `n`).

### **Time Complexity:**

*   **Sliding Window:** O(n), where `n` is the length of the array, as we process each element only once.

*   **Total Time Complexity:** O(n), since the sliding window algorithm is applied twice (once on the original array and once on the concatenated array).

### **Space Complexity:**

*   **Space Complexity:** O(n), due to the concatenated array (`books + books`) and other variables used in the algorithm.

***

### **Variations:**

*   **Fixed Subarray Length:** If instead of maximizing the number of books, you want to find the longest subarray with a fixed length (e.g., a subarray of length `k`), you can adjust the sliding window condition accordingly.

*   **Different Constraints:** If there are additional constraints, such as selecting only books from certain sections of the array (e.g., books from the first half of the array), you can modify the sliding window approach to account for this.
