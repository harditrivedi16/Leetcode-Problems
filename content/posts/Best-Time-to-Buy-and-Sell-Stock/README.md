---
id: 1757e332-de10-803c-a8e1-ed7786900dec
title: Best Time to Buy and Sell Stock
created_time: 2025-01-08T23:19:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Neetcode - 150
  - Top Interview Questions
problem_link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
my_confidence_level: Low
number: 48
last_solved: 2025-01-08T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked:
  - Amazon
  - Google
  - Facebook/Meta
  - Microsoft
  - Morgan Stanley
  - Bloomberg
  - TicTok
  - Salesforce
  - Adobe
problem_name: Best Time to Buy and Sell Stock

---

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxProfit, profit = 0 , 0
        start , end = 0 , 0  # Pointer initialization

        while end < len(prices): 
            # Calculate the profit if we sell at prices[end] and buy at prices[start]
            profit = prices[end] - prices[start]
            
            # If profit is greater than maxProfit, update maxProfit
            if profit >= maxProfit: 
                maxProfit = profit

            # If current price is lower than the start price, move the start pointer
            if prices[end] < prices[start]:
                start = end  # Update the buying day to the current day

            # Move the end pointer to the next day
            end += 1

        return maxProfit 

```

Time Complexity: O(n)

Space Complexity: O(1)
