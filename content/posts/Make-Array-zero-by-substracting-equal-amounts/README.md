---
id: 1df7e332-de10-8077-b980-e73f34cf8c7d
title: Make Array zero by substracting equal amounts
created_time: 2025-04-24T21:25:00.000Z
last_edited_time: 2025-04-29T21:17:00.000Z
difficulty_level: Easy
remarks: no of unique elements = no of operations
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/make-array-zero-by-subtracting-equal-amounts/description/
my_confidence_level: High
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked: []
problem_name: Make Array zero by substracting equal amounts

---

### 🔍 **Intuition**:

We only need to perform an operation for each unique non-zero value in the array. Every operation removes one unique non-zero value.

***

### ✅ **Code**:

```python
python
CopyEdit
class Solution:
    def minimumOperations(self, nums: List[int]) -> int:
        return len(set(nums) - {0})


```

***

### ⏱️ **Time Complexity**:

`O(n)` to build the set from the list.

### 📦 **Space Complexity**:

`O(n)` for storing the unique elements in the set.
