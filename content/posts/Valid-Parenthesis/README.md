---
id: 1e17e332-de10-80db-bf52-c4aa5f96daeb
title: Valid Parenthesis
created_time: 2025-04-26T17:08:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: High
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - Stacks
companies_asked: []
problem_name: Valid Parenthesis

---

**Code**

```python

class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping = {')': '(', '}': '{', ']': '['}

        for char in s:
            if char in mapping.values():  # if it's an opening bracket
                stack.append(char)
            elif char in mapping:  # if it's a closing bracket
                if not stack or stack[-1] != mapping[char]:
                    return False
                stack.pop()
            else:
                # If there are any other characters (optional, depends on constraints)
                return False

        return not stack  # stack should be empty if valid


```

***

### **Intuition Summary:**

We walk through each character:

*   **Opening brackets** are pushed onto a stack.

*   **Closing brackets**: check if the top of the stack matches the corresponding opening bracket.

    *   If yes, pop it.

    *   If no (or stack is empty), the string is invalid.

*   After going through the string, if the stack is empty, it was a valid sequence.

***

### **Time Complexity:**

*   **O(n)** — where `n` is the length of the string `s`.

    (We touch each character once.)

### **Space Complexity:**

*   **O(n)** — in the worst case (all opening brackets), the stack could hold all characters.
