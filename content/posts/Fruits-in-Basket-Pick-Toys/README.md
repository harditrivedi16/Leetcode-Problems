---
id: 1757e332-de10-803c-85d3-c57fe913714f
title: Fruits in Basket/Pick Toys
created_time: 2025-01-08T18:03:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/fruit-into-baskets/description/
my_confidence_level: Meduim
number: 46
amazon_prep: 'No'
last_solved: 2025-01-08T00:00:00.000Z
concept_involved:
  - Sliding Window
companies_asked:
  - Google
  - Amazon
  - Facebook/Meta
problem_name: Fruits in Basket/Pick Toys

---

```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        frequencyMap = {}
        result = 0 
        start, end = 0, 0

        while end < len(fruits): 
            frequencyMap[fruits[end]] = frequencyMap.get(fruits[end], 0 ) + 1
            if len(frequencyMap) <= 2: 
                result = max(result, end - start + 1)
            
            if len(frequencyMap) > 2: 
                frequencyMap[fruits[start]] -= 1
                if frequencyMap[fruits[start]] == 0: 
                    del frequencyMap[fruits[start]]
                start += 1
            
            end += 1
        return result
        
```

Time Complexity: O(n)

Space Complexity: O(2) = O(1)
