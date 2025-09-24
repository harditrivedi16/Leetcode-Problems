---
id: 1e27e332-de10-80c3-b5dd-ca13e5e0aadf
title: Search 2D matrix
created_time: 2025-04-27T17:35:00.000Z
last_edited_time: 2025-05-01T14:30:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Search 2D matrix

---

```python
def searchMatrix(matrix, target):
    # Function to perform binary search on a single row
    def binarySearch(row, target):
        left, right = 0, len(row) - 1
        while left <= right:
            mid = left + (right - left) // 2
            if row[mid] == target:
                return True
            elif row[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return False
    
    for row in matrix:
        if binarySearch(row, target):
            return True
    return False

```

### **Time Complexity:**

*   For each of the `m` rows, we perform binary search on a row of length `n`. So, the overall time complexity is:

    *   `O(m * log n)`

### **Space Complexity:**

*   The space complexity is `O(1)` since we are not using any extra space apart from the input matrix.
