---
id: 2787e332-de10-809b-b99f-f0149fc98c01
title: Design HashMap
created_time: 2025-09-24T15:20:00.000Z
last_edited_time: 2025-09-24T15:21:00.000Z
difficulty_level: Easy
number: 22
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/design-hashmap/description/
my_confidence_level: Meduim
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - HashTables
companies_asked:
  - Amazon
  - Apple
  - Microsoft
  - Goldman Sachs
  - TicTok
problem_name: Design HashMap

---

## Correct Design with Buckets + Chaining

We’ll simulate a real hash map:

*   Use an **array of buckets** (lists).

*   Hash a key to find its bucket index.

*   In each bucket, store `(key, value)` pairs.

*   Handle collisions by **chaining** (list inside each bucket).

***

### Code

```python
class MyHashMap:

    def __init__(self):
        self.size = 1000   # number of buckets
        self.buckets = [[] for _ in range(self.size)]

    def _hash(self, key: int) -> int:
        return key % self.size

    def put(self, key: int, value: int) -> None:
        index = self._hash(key)
        bucket = self.buckets[index]

        for i, (k, v) in enumerate(bucket):
            if k == key:   # update existing key
                bucket[i] = (key, value)
                return
        bucket.append((key, value))  # insert new key

    def get(self, key: int) -> int:
        index = self._hash(key)
        bucket = self.buckets[index]

        for (k, v) in bucket:
            if k == key:
                return v
        return -1   # key not found

    def remove(self, key: int) -> None:
        index = self._hash(key)
        bucket = self.buckets[index]

        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket.pop(i)
                return


```

***

### 🧩 Intuition

*   We mimic how real hash maps work under the hood.

*   Keys are **hashed into buckets**.

*   Each bucket is a list, so collisions are handled by chaining.

*   `put` inserts or updates, `get` searches, and `remove` deletes.

***

### ⏱ Complexity

*   **Time Complexity** (average case):

    *   `put`, `get`, `remove` → **O(1)** average (hashing distributes keys evenly).

    *   Worst case (all keys collide) → O(N), but very rare if size is large.

*   **Space Complexity:** O(N + M)

    *   N = number of keys stored

    *   M = number of buckets

***
