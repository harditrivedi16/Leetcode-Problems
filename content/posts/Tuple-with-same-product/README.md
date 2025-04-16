---
id: 1907e332-de10-8085-9bc8-d343a634c57f
title: Tuple with same product
created_time: 2025-02-04T16:55:00.000Z
last_edited_time: 2025-04-15T16:05:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/tuple-with-same-product/description/
my_confidence_level: Meduim
number: 61
last_solved: 2025-02-05T00:00:00.000Z
concept_involved:
  - HashTables
  - Arrays
companies_asked:
  - Google
problem_name: Tuple with same product

---

```python
class Solution:
    def tupleSameProduct(self, nums: List[int]) -> int:
        product_count = defaultdict(int)

        count = 0 

        for i in range(len(nums)): 
            for j in range(i+1, len(nums)): 
                product = nums[i] * nums[j]
                if product in product_count: 
                    count += product_count[product] * 8
                    product_count[product] += 1
                else: 
                    product_count[product] = 1
                
        return count
        
```

Time Complexity: O(n^2)

Space Complexity: O(nC2)
