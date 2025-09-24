---
id: 1e47e332-de10-80a0-b606-f46de48ea159
title: 'Subset '
created_time: 2025-04-29T18:51:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - BackTracking
companies_asked: []
problem_name: 'Subset '

---

**Problem Statement:**

Given an integer array `nums` of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

**Example:**

Input: `nums = [1,2,3]`

Output:

`[     [],     [1],     [2],     [3],     [1,2],     [1,3],     [2,3],     [1,2,3]   ]`

```python

def subsets(nums):
    result = []
    
    def backtrack(start, path):
        result.append(path)
        for i in range(start, len(nums)):
            backtrack(i + 1, path + [nums[i]])
    
    backtrack(0, [])
    return result

```

Intuition:
The problem is essentially asking us to find all combinations of elements from the input list.
A backtracking approach is a good fit here:

Start with an empty subset.

For each number, either include it in the subset or don't.

This results in exploring all possible subsets through recursive calls.

Time Complexity:
Each element has 2 choices: either include it or exclude it.

Therefore, the number of subsets is 2^n, where n is the number of elements in nums.

The time complexity is O(2^n).

Space Complexity:
We store all subsets, which results in O(2^n) space.

The recursive stack depth can go up to n, so the space complexity is O(2^n) due to the subsets.
