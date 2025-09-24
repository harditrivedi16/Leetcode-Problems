---
id: 2177e332-de10-80bf-ac84-fbd754db1e3a
title: Maximum Subarray
created_time: 2025-06-19T15:10:00.000Z
last_edited_time: 2025-06-22T14:24:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
last_solved: 2025-06-19T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Maximum Subarray

---

Given an array of integers `nums`, find the **contiguous subarray** (containing at least one number) which has the **largest sum**, and return **that sum**.

***

### 🧠 Example:

```python
python
CopyEdit
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6

```

**Is Kadane’s algorithm “greedy”?**

Yes.  At each index it makes an *irrevocable* local choice:

> “Keep extending the current subarray if doing so increases (or at least preserves) its sum; otherwise, discard everything accumulated so far and restart at the current element.”

    That decision is made with no look-ahead and never revisited, which fits the greedy paradigm.

***

### How Kadane’s algorithm works

Variable|Meaning (after processing `a[i]`)
\---|---
`curr`|Best subarray **ending at** `i`
`best`|Best subarray **seen so far**

*   Initialise `curr = best = a[0]`.

*   Scan left-to-right: for each `a[i] (i ≥ 1)`

    ```plain text
    swift
    CopyEdit
    curr = max(a[i], curr + a[i])   // extend or restart
    best = max(best, curr)          // global optimum so far


    ```

*   `best` is the maximum subarray sum.

Both updates are *constant-time*, so the whole pass is **O(n)** with **O(1)** extra space.

***

### Why you can recognise it’s Kadane’s

*   You see only two running variables (`curr`, `best`), updated in a single loop.

*   The key condition `curr = max(a[i], curr + a[i])` (sometimes written with an `if (curr < 0) curr = 0;`) is the tell-tale “drop negative prefix” step.

*   Time complexity is stated as linear with constant memory.

Whenever an interviewer hints “linear‐time, constant-space maximum-sum subarray”, they’re pointing at Kadane.

***

### Reference implementations

### Python

```python

def max_subarray(nums):
    curr = best = nums[0]
    for x in nums[1:]:
        curr = max(x, curr + x)
        best = max(best, curr)
    return best

```
