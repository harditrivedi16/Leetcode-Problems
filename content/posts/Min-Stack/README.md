---
id: 1e17e332-de10-80e8-ab5a-fef4431bcf5a
title: Min Stack
created_time: 2025-04-26T17:25:00.000Z
last_edited_time: 2025-06-23T00:29:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
june_interviews_prep: null
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - Stacks
companies_asked: []
problem_name: Min Stack

---

```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, x: int) -> None:
        self.stack.append(x)
        # If min_stack is empty or current element is smaller or equal to the top of min_stack
        if not self.min_stack or x <= self.min_stack[-1]:
            self.min_stack.append(x)

    def pop(self) -> None:
        if self.stack:
            popped_element = self.stack.pop()
            # If the popped element is the same as the top of min_stack, pop from min_stack as well
            if popped_element == self.min_stack[-1]:
                self.min_stack.pop()

    def top(self) -> int:
        return self.stack[-1] if self.stack else None

    def getMin(self) -> int:
        return self.min_stack[-1] if self.min_stack else None

```

### Explanation:

*   **push(x)**: Adds the element `x` to the main stack. If `x` is less than or equal to the current minimum (top of `min_stack`), we also push it onto `min_stack`.

*   **pop()**: Removes the top element from both the main stack and `min_stack` if it is the current minimum.

*   **top()**: Returns the top element of the main stack.

*   **getMin()**: Returns the top element of the `min_stack`, which is always the minimum element in the stack.

### Time and Space Complexity:

*   **Time Complexity**: All operations (`push()`, `pop()`, `top()`, `getMin()`) take **O(1)** time because each operation involves constant-time interactions with both stacks.

*   **Space Complexity**: The space complexity is **O(n)** where `n` is the number of elements in the stack, since we are maintaining two separate stacks (main stack and `min_stack`).

### Variations:

*   If you want to maintain a **max stack** (to retrieve the maximum element in O(1)), you can follow a similar approach by maintaining a `max_stack` in parallel.

*   Instead of maintaining the minimum in `min_stack`, you could track the difference between the current element and the minimum (for some optimization in specific scenarios).
