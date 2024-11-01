# Container with  Water

Companies asked : Adobe, Amazon, Apple, Bloomberg, Facebook/Meta, Goldman Sachs, Google, Microsoft, Oracle, TicTok, Yahoo
Concept involved: Arrays, Two Pointers
Difficulty level: Meduim 
Last Solved : April 26, 2024
Leetcode Problem List: Blind 75, Neetcode - 150, Top 100 Liked Questions, Top Interview Questions
My Confidence Level : Meduim
Number: 8
Problem Link: https://leetcode.com/problems/container-with-most-water/description/?source=submission-noac

# Container With Most Water

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

### Two Pointer Approach

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:

        max_area = 0 
        i , j = 0 , len(height) - 1

        while i < j: 
            area = (j - i) * min(height[j], height[i])
            max_area = max(area, max_area)

            if height[j] >= height[i]: 
                
                i += 1 

            else: 
                
                j -= 1
    
        return max_area 
        
```

### **Algorithm Explanation**

1. **Initialization**:
    - Initialize two pointers, **`i`** starting at the beginning of the array (**`0`**) and **`j`** at the end (**`len(height) - 1`**).
    - Initialize **`max_area`** to **`0`** to keep track of the maximum area found.
2. **Loop through the array**:
    - While the left pointer **`i`** is less than the right pointer **`j`**:
        - Calculate the area formed between the heights pointed by **`i`** and **`j`** using the formula:
        area=(*j*−*i*)×min(height[*i*],height[*j*])
        where **`(j - i)`** is the distance between the two lines, and **`\min(\text{height}[i], \text{height}[j])`** is the limiting height of the container.
            
            area=(𝑗−𝑖)×min⁡(height[𝑖],height[𝑗])
            
        - Update **`max_area`** if the newly calculated area is greater than the current **`max_area`**.
3. **Move the pointers**:
    - If the height at the right pointer **`j`** is greater than or equal to the height at the left pointer **`i`**, move the left pointer one step to the right (**`i += 1`**). This is because, to potentially find a larger area, we need to try a taller line at the left position since the current left line is shorter or equal.
    - Otherwise, move the right pointer one step to the left (**`j -= 1`**). This is based on the same logic: trying to find a taller line on the right side because the current right line is shorter.
4. **Return the result**:
    - After exiting the loop, return the **`max_area`** which now holds the maximum area of water that can be trapped within two lines of the height array.

### **Time Complexity**

The time complexity of this algorithm is **O(n)**, where **`n`** is the number of elements in the **`height`** array. This is because each element in the array is visited at most once by the two pointers **`i`** and **`j`** moving towards each other from opposite ends of the array. The loop terminates when the two pointers meet, ensuring that each index is processed only once.

### **Space Complexity**

The space complexity of the algorithm is **O(1)**. The space used does not depend on the size of the input array but only on a few additional variables (**`i`**, **`j`**, and **`max_area`**), which use a constant amount of space regardless of the input size.