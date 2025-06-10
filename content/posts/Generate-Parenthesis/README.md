---
id: 1e17e332-de10-801c-8bfa-c1bec591cb1c
title: Generate Parenthesis
created_time: 2025-04-26T17:13:00.000Z
last_edited_time: 2025-04-29T21:19:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: null
june_interviews_prep: null
last_solved: 2025-04-26T00:00:00.000Z
concept_involved:
  - BackTracking
companies_asked: []
problem_name: Generate Parenthesis

---

```python
class Solution:
def generateParenthesis(self, n: int) -> List[str]:
result = []
    
    def backtrack(current, open_count, close_count):
        if len(current) == 2 * n:
            result.append(current)
            return

        if open_count < n:
            backtrack(current + "(", open_count + 1, close_count)
        if close_count < open_count:
            backtrack(current + ")", open_count, close_count + 1)

    backtrack("", 0, 0)
    return result

```

Intuition:
We are building the parentheses string step by step using recursion (backtracking).

We can only add ( if the number of ( we have added so far is less than n.

We can only add ) if the number of ) is less than the number of ( we have already placed (to ensure validity).

When the length of the string reaches 2\*n, it means we used all parentheses, so we add the current string to the result list.

In short: Always maintain validity while building the string.

Time Complexity:

Exponential → O(2^(2n)) in worst case (because at each step we have 2 choices).

But practically it is closer to O(Catalan number) growth, which is approximately O(4^n / sqrt(n)) for n pairs.

Space Complexity:

O(2n) maximum depth of recursion (because each parenthesis contributes 1 character).

O(number of valid combinations × length of each string) for storing all valid answers
