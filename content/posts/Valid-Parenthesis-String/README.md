---
id: 2197e332-de10-80ae-8f7e-f5e04de53860
title: Valid Parenthesis String
created_time: 2025-06-21T19:47:00.000Z
last_edited_time: 2025-06-22T14:32:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-06-21T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Valid Parenthesis String

---

**Problem Statement:**

Given a string `s` containing `'('`, `')'`, and `'*'` — where `'*'` can represent `'('`, `')'`, or an empty string — determine if the string is **valid**.

A valid string has balanced parentheses considering the flexibility of `'*'`.

**Example:**

```python
python
CopyEdit
s = "(*))"
✅ Output: True

```

```python
class Solution:
    def checkValidString(self, s: str) -> bool:
        leftMin, leftMax = 0, 0

        for c in s:
            if c == "(":
                leftMin, leftMax = leftMin + 1, leftMax + 1
            elif c == ")":
                leftMin, leftMax = leftMin - 1, leftMax - 1
            else:
                leftMin, leftMax = leftMin - 1, leftMax + 1
            if leftMax < 0:
                return False
            if leftMin < 0:
                leftMin = 0
        return leftMin == 0
```
