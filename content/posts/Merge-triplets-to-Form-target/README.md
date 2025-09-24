---
id: 2197e332-de10-801a-9b43-e45b4c8ef5a4
title: Merge triplets to Form target
created_time: 2025-06-21T19:46:00.000Z
last_edited_time: 2025-06-22T14:30:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-06-21T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Merge triplets to Form target

---

Given a list of triplets (each with 3 integers), and a target triplet `[x, y, z]`, determine if **some combination** of these triplets can be merged to form the target — where:

*   You can pick triplets with values ≤ target in each index.

*   A merged triplet takes the **maximum** value at each index across chosen triplets.

**Return:** `True` if it's possible to form the exact target, else `False`.

```python
class Solution:
    def mergeTriplets(self, triplets: List[List[int]], target: List[int]) -> bool:
        good = set()

        for t in triplets:
            if t[0] > target[0] or t[1] > target[1] or t[2] > target[2]:
                continue
            for i, v in enumerate(t):
                if v == target[i]:
                    good.add(i)
        return len(good) == 3
```
