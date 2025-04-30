---
id: 1e47e332-de10-8095-bdde-da3b98aeafa0
title: Evaluate Boolean Parenthesization
created_time: 2025-04-29T17:24:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Dynamic Programming
companies_asked: []
problem_name: Evaluate Boolean Parenthesization

---

You are given a string `s` consisting of characters `'T'` (True), `'F'` (False), and operators `'&'`, `'|'`, and `'^'` (AND, OR, XOR, respectively). Your task is to compute the number of ways to parenthesize the expression so that the result evaluates to `True`.

**Example:**

Input: `"T|F&T^F"`

Output: `4`

Explanation: There are four ways to parenthesize the expression so that it evaluates to `True`.

```python
def solve(s: str, i: int, j: int, isTrue: bool, memo: dict) -> int:
    if i > j:
        return 0

    if i == j:
        if isTrue:
            return 1 if s[i] == 'T' else 0
        else:
            return 1 if s[i] == 'F' else 0

    key = (i, j, isTrue)
    if key in memo:
        return memo[key]

    ans = 0

    for k in range(i + 1, j, 2):  # k is the operator index
        op = s[k]

        # Recursive calls
        LT = solve(s, i, k - 1, True, memo)
        LF = solve(s, i, k - 1, False, memo)
        RT = solve(s, k + 1, j, True, memo)
        RF = solve(s, k + 1, j, False, memo)

        if op == '&':
            if isTrue:
                ans += LT * RT
            else:
                ans += (LT * RF) + (LF * RT) + (LF * RF)

        elif op == '|':
            if isTrue:
                ans += (LT * RT) + (LT * RF) + (LF * RT)
            else:
                ans += (LF * RF)

        elif op == '^':
            if isTrue:
                ans += (LT * RF) + (LF * RT)
            else:
                ans += (LT * RT) + (LF * RF)

    memo[key] = ans
    return ans

```

### How the approach works:

*   **Recursive thinking**:

    We take a portion of the string and recursively try **all possible places to put parentheses** (every operator is a split point).

*   **Split into left and right**:

    For every operator (like `|`, `&`, `^`), we split the string into:

    *   Left part (before operator)

    *   Right part (after operator)

*   **Evaluate both sides**:

    For both left and right parts, we calculate:

    *   How many ways they can be `True`

    *   How many ways they can be `False`

*   **Apply operator rules**:

    Depending on the operator and whether we want the result to be `True` or `False`, we combine the left and right counts accordingly:

    *   For `&`, we need both sides to be `True` to make the result `True`

    *   For `|`, even one `True` is enough

    *   For `^`, the result is `True` if the sides are **different**

*   **Memoization**:

    Since we solve the same subproblems again and again, we use a dictionary to **store already computed results** and save time.

*   **Add all valid combinations**:

    For each possible split, we keep adding the number of ways that result in `True`.

### **Time Complexity:**

We memoize results for each `(i, j, isTrue)` triple. Let’s see how many such combinations are possible:

*   `i` and `j` can range from `0` to `n-1` → There are `O(n²)` such pairs.

*   For each `(i, j)`, we evaluate both `isTrue = True` and `isTrue = False` → That doubles the combinations.

✅ So total subproblems = `O(n² * 2)` = `O(n²)`

But for each subproblem, we may try every operator between `i` and `j`, and the number of operators is approximately `n/2` (since operators occur at every odd index).

❌ So each subproblem takes `O(n)` time to solve.

### ✅ Final Time Complexity:

**`O(n³)`**, where `n` is the length of the expression.

***

### 💾 **Space Complexity:**

*   **Recursion stack**: Can go as deep as `O(n)` (in worst case, when we keep splitting into smaller parts).

*   **Memoization dictionary**: Stores results for `O(n²)` subproblems.

### ✅ Final Space Complexity:

**`O(n²)`** for memoization + `O(n)` for recursion stack = **`O(n²)`**
