---
id: 1e17e332-de10-8070-aa27-d5b72d2ad7a2
title: Sum of Total strength of Wizards
created_time: 2025-04-26T17:26:00.000Z
last_edited_time: 2025-04-26T18:15:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: 143
amazon_prep: 'Yes'
last_solved: 2025-04-26T00:00:00.000Z
concept_involved: []
companies_asked: []
problem_name: Sum of Total strength of Wizards

---

Note this is very hard problem and you only know the bruteforce, and half of the intuition.

```python
class Solution:
    def totalStrength(self, strength: List[int]) -> int:
        
        res = 0
        for i in range(len(strength)):
            for j in range(i + 1, len(strength) + 1):
                res += (min(strength[i:j]) * sum(strength[i:j]))
        return res
```

this is brute force, but it has time complexity iof O(n^2) and since n is very long, it may exceed time limit.

So there is a way to optimize it, and I only figured out half of it.

*   we use stack to find the range of all sub arrays where the given element will be minimum NSR- NSL.

Now the sol would for that ele will be min \* Sum of all subarrays\[]- we can use prefix sum to find that but I can’t figure out how?
