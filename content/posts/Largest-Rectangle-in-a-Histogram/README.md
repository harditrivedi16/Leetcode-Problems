---
id: 1e17e332-de10-8028-a3a9-f012a63889a1
title: Largest Rectangle in a Histogram
created_time: 2025-04-26T16:19:00.000Z
last_edited_time: 2025-05-01T14:42:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: High
number: 33
amazon_prep: 'Yes'
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - Stack
companies_asked: []
problem_name: Largest Rectangle in a Histogram

---

```python
class LargestRectangleHistogram:
    def __init__(self, heights):
        self.heights = heights
        self.n = len(heights)

    def nextSmallerToLeft(self):
        stack = []
        nsl = [-1] * self.n
        for i in range(self.n):
            while stack and self.heights[stack[-1]] >= self.heights[i]:
                stack.pop()
            if stack:
                nsl[i] = stack[-1]
            stack.append(i)
        return nsl

    def nextSmallerToRight(self):
        stack = []
        nsr = [self.n] * self.n
        for i in range(self.n - 1, -1, -1):
            while stack and self.heights[stack[-1]] >= self.heights[i]:
                stack.pop()
            if stack:
                nsr[i] = stack[-1]
            stack.append(i)
        return nsr

    def largestRectangleArea(self):
        nsl = self.nextSmallerToLeft()
        nsr = self.nextSmallerToRight()
        
        max_area = 0
        for i in range(self.n):
            width = nsr[i] - nsl[i] - 1
            area = width * self.heights[i]
            max_area = max(max_area, area)
        
        return max_area

```

###

Time and Space Complexity:

### Explanation:

*   **`__init__(self, heights)`**:

    The constructor initializes the object with the list `heights` and calculates its length `n`.

*   **`nextSmallerToLeft(self)`**:

    This method finds the index of the nearest smaller element to the left of each bar (same as the function we had earlier).

*   **`nextSmallerToRight(self)`**:

    This method finds the index of the nearest smaller element to the right of each bar (again, same logic as before).

*   **`largestRectangleArea(self)`**:

    This method calculates and returns the maximum area of the rectangle that can be formed in the histogram using the previously defined methods for NSL and NSR.

*   **Time Complexity:**

    *   The methods `nextSmallerToLeft` and `nextSmallerToRight` each run in O(n) time, and the final iteration also takes O(n).

    *   **Overall: O(n)**

*   **Space Complexity:**

    *   The class uses O(n) space for `nsl`, `nsr`, and the stack.

    *   **Overall: O(n)**
