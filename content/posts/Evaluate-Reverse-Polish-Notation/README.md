---
id: 1e17e332-de10-80e0-b2e8-cdcf7140c2fa
title: Evaluate Reverse Polish Notation
created_time: 2025-04-26T16:15:00.000Z
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
problem_name: Evaluate Reverse Polish Notation

---

### **Intuition:**

We’ll solve this problem using a **stack**. The key idea is that **Reverse Polish Notation (RPN)** evaluates in a left-to-right order. Here’s how it works:

*   **Push operands (numbers)** onto the stack.

*   When an operator is encountered, **pop the last two operands** from the stack, apply the operator, and **push the result back onto the stack**.

*   Continue this until the entire expression is evaluated.

*   The stack will hold the final result once all tokens have been processed.

### **Approach:**

*   We will iterate through the `tokens` list.

*   If the token is a number, we push it onto the stack.

*   If the token is an operator, we pop the last two numbers, apply the operator, and push the result back onto the stack.

*   The final result will be the last element left in the stack.

***

### **Code Implementation:**

```python
python
CopyEdit
def evalRPN(tokens):
    stack = []

    # Define the operators
    operators = {'+', '-', '*', '/'}

    for token in tokens:
        if token not in operators:
            # If the token is a number, push it onto the stack
            stack.append(int(token))
        else:
            # If the token is an operator, pop two numbers, apply operator and push result
            b = stack.pop()
            a = stack.pop()

            if token == '+':
                stack.append(a + b)
            elif token == '-':
                stack.append(a - b)
            elif token == '*':
                stack.append(a * b)
            elif token == '/':
                # Integer division with truncation towards zero
                stack.append(int(a / b))  # Python's int() truncates towards zero

    # The result is the last element on the stack
    return stack[0]


```

***

### **Example Walkthrough:**

Let’s take the example expression: `["2", "1", "+", "3", "*"]`

*   Process `2` → Push `2` onto the stack → `stack = [2]`

*   Process `1` → Push `1` onto the stack → `stack = [2, 1]`

*   Process `+` → Pop `1` and `2` → `2 + 1 = 3` → Push `3` onto the stack → `stack = [3]`

*   Process `3` → Push `3` onto the stack → `stack = [3, 3]`

*   Process  → Pop `3` and `3` → `3 * 3 = 9` → Push `9` onto the stack → `stack = [9]`

*   Final result is `9`.

***

### **Time and Space Complexity:**

*   **Time Complexity:**

    *   We iterate through the `tokens` list once and each operation (push, pop, and arithmetic) takes O(1) time.

    *   **Overall Time Complexity:** O(n), where n is the number of tokens.

*   **Space Complexity:**

    *   We use a stack to store numbers, which will hold at most n/2 numbers at any time (since every operator consumes two operands).

    *   **Overall Space Complexity:** O(n)

***

### **Possible Variations:**

*   **Floating Point Division:**

    If you have floating-point division, you can modify the code to handle float division instead of integer truncation.

*   **Handling Negative Numbers:**

    The code assumes that negative numbers are valid operands and uses `int()` for truncation (Python handles this well).

*   **Edge Cases:**

    *   Empty expression: Can handle by checking the length of tokens.

    *   Division by zero: You can add extra validation if needed.
