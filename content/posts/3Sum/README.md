---
id: 1317e332-de10-8132-94ac-c64a8bdafb73
title: 3Sum
created_time: 2024-11-01T16:01:00.000Z
last_edited_time: 2025-10-15T18:09:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Top 100 Liked Questions
  - Top Interview Questions
  - Neetcode - 150
  - Blind 75
  - Top Microsoft Questions
problem_link: https://leetcode.com/problems/3sum/description/
my_confidence_level: High
last_solved: null
concept_involved:
  - Arrays
  - Two Pointers
companies_asked:
  - Facebook/Meta
  - Amazon
  - Adobe
  - Apple
  - Google
  - Microsoft
  - Agoda
  - Bloomberg
  - Yahoo
  - TicTok
  - Intuit
  - Nvidia
problem_name: 3Sum

---

# 3Sum

## Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.Notice that the solution set must not contain duplicate triplets.

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []

        nums.sort()

        for i, a in enumerate(nums): 
            if i > 0 and a == nums[i-1]:
                i += 1
                continue 
            l, r = i + 1 , len(nums) - 1

            while l < r : 
                sum = a + nums[l] + nums[r]

                if sum > 0 :
                    r -= 1
                elif sum < 0 :
                    l += 1
                   
                else: 
                    res.append([a, nums[l], nums[r]]) 
                    l += 1
                    #r -= 1
                    while nums[l] == nums[l-1] and l < r:
                        l += 1   

                

        return res      
```

The 3Sum problem involves finding all unique triplets in the array which gives the sum of zero. The solution provided is a Python method that implements a two-pointer approach to solve the 3Sum problem. Here is the logic and explanation:

*   **Sort the array**: This allows two pointers to approach each other from opposite ends of the array to find the correct triplets.

*   **Iterate with a for-loop**: The loop goes through each element **`a`** as a potential first element of the triplet.

*   **Skip duplicates for the first element**: If the current element is the same as the previous one, we skip it to avoid duplicate triplets.

*   **Initialize two pointers**: **`l`** (left) is set to **`i+1`**, and **`r`** (right) is set to the last index.

*   **Two pointers iteration**: While **`l`** is less than **`r`**, check the sum of the current triplet.

    *   If the sum is greater than 0, decrement **`r`** to reduce the sum.

    *   If the sum is less than 0, increment **`l`** to increase the sum.

    *   If the sum is 0, we found a triplet:

        *   Add it to the results list.

        *   Increment **`l`** to move to the next different number.

        *   If the next number is the same as the previous, we keep incrementing **`l`** to avoid duplicates (handled in the while loop).

The last else section specifically handles when a valid triplet summing to zero is found. The triplet is added to the result list, and then the left pointer **`l`** is moved right to the next unique number to continue searching for other triplets. This is done by incrementing **`l`** and then using a while loop to skip over any duplicate numbers that follow.

**Basic Syntax Definitions**:

*   **`sort()`**: This method sorts the list in ascending order.

*   **`enumerate()`**: This function adds a counter to an iterable and returns it as an enumerate object.

**Time Complexity**: The time complexity of this function is 𝑂(𝑛^2). The array is sorted once 𝑂(𝑛log⁡𝑛), and then the for-loop combined with the two-pointer search results in 𝑂(𝑛^2). so nlogn + n^2 give n^2

**Space Complexity**: The space complexity is 𝑂(1)if the output array does not count towards space complexity, since no additional space is required beyond the input array and pointers. If the output array is considered, the space complexity would be 𝑂(𝑛)*O*(*n*) for the output, where 𝑛\_n\_ is the number of unique triplets.
