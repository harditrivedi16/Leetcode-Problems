---
id: 1317e332-de10-81e2-9ee2-d7f0c95763e1
title: Trapping Rain Water
created_time: 2024-11-01T16:01:00.000Z
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
problem_name: Trapping Rain Water

---

```python
def trap(height):
    n = len(height)
    if n < 3:
        return 0  # No space to trap water if fewer than 3 bars

    # Helper function to calculate NGL (Next Greater Left) for each index
    def calculate_NGL(height):
        stack = []
        NGL = [0] * len(height)
        for i in range(len(height)):
            while stack and height[i] >= height[stack[-1]]:
                stack.pop()
            if stack:
                NGL[i] = stack[-1]
            stack.append(i)
        return NGL

    # Helper function to calculate NGR (Next Greater Right) for each index
    def calculate_NGR(height):
        stack = []
        NGR = [0] * len(height)
        for i in range(len(height) - 1, -1, -1):
            while stack and height[i] >= height[stack[-1]]:
                stack.pop()
            if stack:
                NGR[i] = stack[-1]
            stack.append(i)
        return NGR

    # Calculate NGL and NGR for each index
    NGL = calculate_NGL(height)
    NGR = calculate_NGR(height)

    # Calculate the total amount of trapped water
    total_water = 0
    for i in range(1, n - 1):
        # The trapped water is determined by the height of the smaller bar
        water_at_i = min(height[NGL[i]], height[NGR[i]]) - height[i]
        if water_at_i > 0:
            total_water += water_at_i

    return total_water

```

### **Explanation:**

*   **NGL Calculation:**

    *   For each index `i`, the `while` loop pops indices from the stack while the current bar is taller than the bar at the top of the stack. If the stack is not empty after that, the top element of the stack represents the nearest taller bar to the left.

*   **NGR Calculation:**

    *   This is similar to NGL, but we iterate over the array in reverse order (right to left) to find the nearest taller bar to the right.

*   **Water Calculation:**

    *   For each index, we use the values from the `NGL` and `NGR` arrays to find the trapped water using the formula:water at index=min(height of NGL\[i],height of NGR\[i])−height\[i]

        water at index=min⁡(height of NGL\[i],height of NGR\[i])−height\[i]\text{water at index} = \min(\text{height of NGL\[i]}, \text{height of NGR\[i]}) - \text{height\[i]}

        If this value is positive, we add it to the total water.

### **Time Complexity:**

*   **NGL Calculation:** O(n)

*   **NGR Calculation:** O(n)

*   **Water Calculation:** O(n)

*   **Total Time Complexity:** O(n)

### **Space Complexity:**

*   **Space Complexity:** O(n), as we use two extra arrays (`NGL` and `NGR`).
