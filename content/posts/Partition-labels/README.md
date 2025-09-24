---
id: 2197e332-de10-806c-9f39-d2e9ea43f8e2
title: Partition labels
created_time: 2025-06-21T19:46:00.000Z
last_edited_time: 2025-06-22T14:31:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-06-21T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Partition labels

---

### 🧩 **Partition Labels**

**Problem Statement:**

Given a string `s`, partition it into as many parts as possible such that **each letter appears in at most one part**.

**Return:** A list of the lengths of these partitions.

```python
class Solution:
    def partitionLabels(self, s: str) -> List[int]:
        lastIndex = {}
        for i, c in enumerate(s):
            lastIndex[c] = i

        res = []
        size = end = 0
        for i, c in enumerate(s):
            size += 1
            end = max(end, lastIndex[c])

            if i == end:
                res.append(size)
                size = 0
        return res
```
