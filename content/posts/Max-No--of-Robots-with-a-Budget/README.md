---
id: 1e27e332-de10-8057-9be5-dd5e2b84e536
title: Max No. of Robots with a Budget
created_time: 2025-04-27T17:00:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Max No. of Robots with a Budget

---

### **Code Implementation:**

```python

def maxRobots(cost, capacity, budget):
    # Sort the robots based on their cost
    robots = sorted(zip(cost, capacity))

    total_cost = 0
    max_robots = 0

    # Iterate over the sorted robots and keep adding them until budget is exceeded
    for i in range(len(robots)):
        total_cost += robots[i][0]
        if total_cost <= budget:
            max_robots += 1
        else:
            break

    return max_robots


```

### **Explanation:**

*   **Sorting**:

    We use `zip(cost, capacity)` to pair up each robot’s cost and capacity, and then sort these pairs based on cost in ascending order. This ensures we consider the cheaper robots first, which maximizes the number of robots we can afford.

*   **Total Cost Calculation**:

    We start adding the cost of each robot one by one. If adding the robot’s cost exceeds the budget, we stop and return the number of robots we’ve bought so far.

*   **Greedy Buying**:

    This greedy strategy ensures that we always purchase the least expensive robots first, thereby maximizing the number of robots we can afford.

### **Time Complexity:**

*   **Sorting the robots** takes `O(n log n)`.

*   **Iterating through the sorted list** to calculate the total cost is `O(n)`.

Thus, the overall time complexity is:

**O(n log n)** due to sorting.

### **Space Complexity:**

*   **O(n)** for storing the sorted list of robots.
