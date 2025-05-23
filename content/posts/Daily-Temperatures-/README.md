---
id: 1317e332-de10-81e1-bde3-c14928a129de
title: 'Daily Temperatures '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:04:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
problem_link: https://leetcode.com/problems/daily-temperatures/description/
my_confidence_level: Meduim
number: 20
last_solved: 2024-10-11T00:00:00.000Z
concept_involved:
  - Stack
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
  - Microsoft
  - Zoho
  - Octa
  - Anduril
problem_name: 'Daily Temperatures '

---

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:

        stack = []
        res = [0] * len(temperatures)

        for i in range(len(temperatures)-1, -1, -1): 

            while stack and temperatures[i] >= stack[-1][1]: 
                stack.pop()
            if stack: 
                res[i] = stack[-1][0] - i 
            stack.append((i,temperatures[i]))

        return res 
        
```

*   The code utilizes a stack to efficiently track the indices and values of temperatures, allowing it to calculate the number of days until a warmer temperature for each day by iterating through the list from right to left.

*   For each temperature, it pops elements from the stack that are not warmer and, if the stack is not empty after this process, calculates the difference in indices to determine how many days until a warmer temperature.

**Time Complexity**: O(n), where n is the number of temperatures.

**Space Complexity**: O(n) for the stack and result list.
