---
id: 2787e332-de10-80ee-b730-edbc15013e45
title: Design Hashset
created_time: 2025-09-24T15:13:00.000Z
last_edited_time: 2025-09-24T15:14:00.000Z
difficulty_level: Easy
number: 21
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/design-hashset/description/
my_confidence_level: High
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - Sets
companies_asked:
  - Google
problem_name: Design Hashset

---

We want a simple `HashSet`. The easiest way in Python is to use a **set** internally:

```python
class MyHashSet:

    def __init__(self):
        self.hash_set = set()   # initialize empty set

    def add(self, key: int) -> None:
        self.hash_set.add(key)  # add to set

    def remove(self, key: int) -> None:
        if key in self.hash_set:
            self.hash_set.remove(key)  # safely remove if exists

    def contains(self, key: int) -> bool:
        return key in self.hash_set   # membership check


```

***

### 🧩 Intuition

*   A **set** is the natural data structure for a `HashSet`.

*   Internally, Python sets use **hashing**, so operations like `add`, `remove`, and `contains` are **O(1) average case**.

*   We don’t care about order, only uniqueness and membership.

***

### ⏱ Complexity

*   **Time Complexity**:

    *   `add(key)` → O(1) average

    *   `remove(key)` → O(1) average

    *   `contains(key)` → O(1) average

*   **Space Complexity**: O(N)

    *   N = number of keys stored.
