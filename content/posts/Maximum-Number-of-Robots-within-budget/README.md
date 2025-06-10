---
id: 1e47e332-de10-8086-b1d4-f4c264d072df
title: Maximum Number of Robots within budget
created_time: 2025-04-29T14:43:00.000Z
last_edited_time: 2025-05-01T14:40:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: High
number: 28
june_interviews_prep: null
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked: []
problem_name: Maximum Number of Robots within budget

---

```python
class Solution:
    def maxRobots(self, costs: List[int], budget: int) -> int:
        maxRobots = 0
        currentCost = 0
        start = 0
        
        for end in range(len(costs)):
            currentCost += costs[end]
            
            while currentCost > budget:  # Shrink the window if the cost exceeds the budget
                currentCost -= costs[start]
                start += 1
                
            maxRobots = max(maxRobots, end - start + 1)  # Update the max number of robots
            
        return maxRobots

```

Maximum Number of Robots Within Budget:
You are given an array costs\[] where costs\[i] represents the cost of the ith robot, and a budget budget. You need to find the maximum number of robots that can be bought such that the total cost does not exceed the budget. The robots must be bought in consecutive order.

### Intuition:

*   You maintain a sliding window (with `start` and `end` pointers) and expand the window by moving `end`.

*   If the total cost exceeds the budget, you increment `start` to shrink the window until the cost is within the budget.

*   At each step, you check the number of robots that can be bought and update the result with the maximum possible count.

time complexity: O(n) and space complexity: O(1)
