---
id: 1e27e332-de10-80d0-b88e-fe7dc473c072
title: Count of smaller No. after self
created_time: 2025-04-27T16:54:00.000Z
last_edited_time: 2025-05-01T14:30:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 11
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Count of smaller No. after self

---

```python
def countSmaller(nums):
    # Result array to store the answer
    result = []
    
    # A sorted list where we will keep elements in order as we process them
    sorted_list = []
    
    # Helper function to perform binary search
    def binary_search(sorted_list, target):
        left, right = 0, len(sorted_list) - 1
        while left <= right:
            mid = (left + right) // 2
            if sorted_list[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left
    
    # Traverse the original list in reverse (right to left)
    for num in reversed(nums):
        # Find the index where 'num' should be inserted in the sorted list
        index = binary_search(sorted_list, num)
        
        # The index tells us how many numbers are smaller than the current element
        result.append(index)
        
        # Insert the number into the sorted list (keeping the list sorted)
        sorted_list.insert(index, num)
    
    # Since we processed the numbers in reverse order, reverse the result to match original order
    return result[::-1]

```

### **Complexity**:

*   **Time Complexity**: O(n^2) — For each number, we perform a binary search (`O(log n)`) and then insert it (`O(n)`) into the `sorted_list`. In total, for `n` elements, this gives us a time complexity of `O(n^2)`.

*   **Space Complexity**: O(n) — We store the result and the sorted list.
