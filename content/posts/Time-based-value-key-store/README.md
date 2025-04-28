---
id: 1e27e332-de10-80b3-9dce-d1c8763b6527
title: Time based value key store
created_time: 2025-04-27T17:36:00.000Z
last_edited_time: 2025-04-27T17:43:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 155
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
  - Design
companies_asked: []
problem_name: Time based value key store

---

```python
import bisect

class TimeMap:

    def __init__(self):
        self.store = {}

    def set(self, key: str, value: str, timestamp: int) -> None:
        if key not in self.store:
            self.store[key] = []
        self.store[key].append((value, timestamp))

    def get(self, key: str, timestamp: int) -> str:
        if key not in self.store:
            return ""
        
        values = self.store[key]
        # Use binary search to find the largest timestamp <= the given timestamp
        i = bisect.bisect_right(values, (None, timestamp)) - 1
        
        # If the index is valid, return the corresponding value, otherwise return ""
        if i >= 0:
            return values[i][0]
        return ""

```

### **Time Complexity:**

*   **`set(key, value, timestamp)`**: `O(1)` (appending to the list).

*   **`get(key, timestamp)`**: `O(log n)` where `n` is the number of stored timestamp-value pairs for the given key. This is because of the binary search using `bisect_right`, which operates in logarithmic time.

### **Space Complexity:**

*   The space complexity is `O(n)` where `n` is the total number of timestamp-value pairs stored in the system. Each pair is stored in a list for each key.

### **Understanding** **`bisect.bisect_right`\*\*\*\*:**

The function `bisect.bisect_right` is used to find the insertion position for a given element in a sorted list, such that all elements before the insertion point are less than or equal to the given element.

### **Syntax:**

```python
python
CopyEdit
bisect.bisect_right(list, element, lo=0, hi=len(list))


```

*   **`list`**: The sorted list where we want to find the insertion position.

*   **`element`**: The element that we want to insert or search for in the list.

*   **`lo`** (optional): The starting index to consider for the search (default is 0).

*   **`hi`** (optional): The ending index to consider for the search (default is `len(list)`).

### **What does** **`bisect_right`** **do?**

`bisect_right` returns the index where the given `element` would fit in the list to maintain sorted order **if we inserted the element into the list**. It places the `element` to the **right** of any existing equal elements.
