# Daily Temperatures

Companies asked : Amazon, Anduril, Facebook/Meta, Google, Microsoft, Octa, Zoho
Concept involved: Stack
Difficulty level: Meduim 
Last Solved : October 11, 2024
Leetcode Problem List: Neetcode - 150, Top 100 Liked Questions
My Confidence Level : Meduim
Number: 20
Problem Link: https://leetcode.com/problems/daily-temperatures/description/

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

1. The code utilizes a stack to efficiently track the indices and values of temperatures, allowing it to calculate the number of days until a warmer temperature for each day by iterating through the list from right to left.
2. For each temperature, it pops elements from the stack that are not warmer and, if the stack is not empty after this process, calculates the difference in indices to determine how many days until a warmer temperature.

**Time Complexity**: O(n), where n is the number of temperatures.

**Space Complexity**: O(n) for the stack and result list.