---
id: 1e17e332-de10-8070-aa27-d5b72d2ad7a2
title: Sum of Total strength of Wizards
created_time: 2025-04-26T17:26:00.000Z
last_edited_time: 2025-04-29T21:16:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - Stack
  - PrefixSum
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

Problem:

You are given an array strength of size n, where each element strength\[i] represents the strength of the i-th wizard.

For each wizard, calculate the total strength of all possible subarrays that have the wizard as the minimum strength. The sum of all these subarray strengths across all wizards will give you the total strength.

More formally:
For every wizard i, calculate the sum of strengths of all subarrays where the wizard i is the minimum element. Then, sum these values for all the wizards to find the final result.
