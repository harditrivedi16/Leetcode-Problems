---
id: 1e17e332-de10-80de-a6b6-eceb4d9e8919
title: Sum of SubArray Ranges
created_time: 2025-04-26T17:00:00.000Z
last_edited_time: 2025-05-01T14:42:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: 34
june_interviews_prep: null
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - Stack
  - PrefixSum
companies_asked: []
problem_name: Sum of SubArray Ranges

---

```python
class Solution:
    def subArrayRanges(self, nums: List[int]) -> int:
        n, answer = len(nums), 0 
        stack = []
        
        # Find the sum of all the minimum.
        #Monotonically increasing stack 1 -> 2 -> 3 -> 4 top smallest element
        for right in range(n + 1):
            while stack and (right == n or nums[stack[-1]] >= nums[right]):
                mid = stack.pop()
                left = -1 if not stack else stack[-1]
                answer -= nums[mid] * (mid - left) * (right - mid)
            stack.append(right)

        # Find the sum of all the maximum.
        stack.clear()
        for right in range(n + 1):
            while stack and (right == n or nums[stack[-1]] <= nums[right]):
                mid = stack.pop()
                left = -1 if not stack else stack[-1]
                answer += nums[mid] * (mid - left) * (right - mid)
            stack.append(right)
        
        return answer
```

### **Intuition**

From the definition of the sum of all subarray ranges:

*k\_∑\_rangek*=\_k\_∑(*maxValk\_−\_minValk*)=*k\_∑\_maxValk\_−\_k\_∑\_minValk*

> It implies that we can calculate these two partial sums separately.

Let's think of this problem differently, instead of finding each subarray and getting its `minVal` and `maxVal`, we focus on each number. If we can find that, for each number `nums[i]`, the number of subarrays having `nums[i]` as its **minimum value** is `minTime[i]`. Then the sum of `minVal` can be rewritten as:

*∑minValk=∑minTime\[i] ⋅ nums\[i]*

For example, we have found `minTime = [1, 4, 1]` for the array `[X, Y, Z]` by some means (which will be explained in detail soon), then the sum of `minVal` is `1 * X + 4 * Y + 1 * Z`. We don't need to know exactly which array holds which value as the minimum, but only the number of times each number is taken as the minimum!

> Now the task becomes finding minTime\[i] for each index i.

Notice that `minTime[i]` depends on:

*   The number of consecutive elements **larger than or equal to** `nums[i]` on its left side. In other words, to find the index `left` where the value is **less than** `nums[i]`.

*   The number of consecutive elements **larger than or equal to** `nums[i]` on its right side. In other words, to find the index `right` where the value is **strictly less than** `nums[i]`.

Now we have (i - left) positions to put the starting position of the subarray, and (right - i) positions to put the ending position of the subarray. Therefore, we have (i - left) \* (right - i) valid subarrays in total, so we can calculate `minTime[i]` as follows:

*minTime*\[*i*]=(*right\_−\_i*)⋅(*i\_−\_left*)

*rangei*=*minTime*\[*i*]⋅\_nums\_\[*i*]

In the array shown below, `nums[3] = 4` has `left = 0` and `right = 6`, thus the number of subarrays having `nums[3]` as the minimum is `minTime[3] = (6 - 3) * (3 - 0) = 9`, meaning that there are 9 subarays having `nums[3]` as the minimum.

**Algorithm**

*   Initialize an empty stack `stack`, get the size of `nums` as `n`.

*   Iterate over every index from `0` to `n` (inclusive). For each index `right`, if either of the following two condition is met:

    *   `index = n`

    *   `stack` is not empty and `nums[mid] >= nums[right]`, where `mid` is its top value:

    go to step 3.

    Otherwise, repeat step 2.

*   Calculate the number of subarrays with `nums[mid]` as its minimum value:

    *   Pop `mid` from stack.

    *   If `stack` is empty, set `left = -1`, otherwise, `left` equals the top element from `stack`.

    *   Increment `answer` by `(right - mid) * (mid - left)`.

    *   Repeat step 2.

The condition `right == n` inside the `while` loop is **very important** for both minimum and maximum calculations.

Let me explain simply:

*   `right` is moving from `0` to `n` (we intentionally go up to `n`, not `n-1`).

*   `nums` has valid indices `0` to `n-1`, so when `right == n`, it’s **out of bounds**.

*   But **we still need to empty the stack** at the end because there could be elements left in the stack that didn’t find their "next smaller" or "next greater" element naturally.

*   Setting `right == n` forces the remaining elements in the stack to **pop out** and complete their contribution calculations.

**In short:**

👉 `right == n` is a trick to *flush the stack* at the end of the array.

### **Implementation**

### **Complexity Analysis**

Let *n* be the size of the input array `nums`.

*   Time complexity: *O*(*n*)

    *   To find the total sum of `minVal`, we only need one iteration over `nums`, and each number will be added to and popped from `stack` once, these also apply for finding `maxVal`.

    *   Therefore the overall time complexity is *O*(*n*).

*   Space complexity: *O*(*n*)

    *   We use a (monotonic) stack to keep the increasing (decreasing) sequence, in the worst-case scenario, there may be *O*(*n*) numbers in the stack, which takes *O*(*n*) space.
