---
id: 1317e332-de10-81c9-9f0a-ce121140e80c
title: 'Two Sum '
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-04-15T16:03:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top 100 Liked Questions
  - Blind 75
  - Top Interview Questions
problem_link: https://leetcode.com/problems/two-sum/description/
my_confidence_level: High
number: 3
last_solved: 2024-12-01T00:00:00.000Z
concept_involved:
  - Arrays
  - HashTables
companies_asked:
  - Amazon
  - Google
  - Apple
  - Adobe
  - Microsoft
  - Bloomberg
  - Facebook/Meta
  - Uber
  - Oracle
  - Yandex
  - Yahoo
  - Goldman Sachs
  - IBM
  - TicTok
  - Morgan Stanley
  - Cisco
  - Zoho
  - Nvidia
  - JPMorgan
  - DoorDash
problem_name: 'Two Sum '

---

## Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to* *`target`*. You may assume that each input would have ***exactly*** **one solution**, and you may not use the *same* element twice. You can return the answer in any order.

### Hash Approach

```python
**class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap = {}
        for i in range(len(nums)):
            complement = target - nums[i]
            if complement in hashmap:
                return [i, hashmap[complement]]
            hashmap[nums[i]] = i**
```

**Explanation:** Now as we know, Hash table has dynamic search and insert options to search an element we have to pass through an entire array making Big O :O(n), but in hash table it is O(1).
While we are iterating and inserting elements into the hash table, we also look back to check if current element's complement already exists in the hash table. If it exists, we have found a solution and return the indices immediately.

\*\*Time Complexity: O(n)\*\*Traverse through the whole array while creating the hastable.

**Space Complexity: O(n)** In worst case scenario, the entire array is stored in hastable, we introduce a new data structure of size n
