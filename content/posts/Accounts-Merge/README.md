---
id: 1db7e332-de10-8036-92f2-f34c9865088a
title: Accounts Merge
created_time: 2025-04-20T01:59:00.000Z
last_edited_time: 2025-10-15T18:13:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/account...
my_confidence_level: Low
last_solved: null
concept_involved:
  - Graphs
companies_asked: []
problem_name: Accounts Merge

---

```python
from collections import defaultdict

class UnionFind:
    def __init__(self):
        self.parent = {}  # Maps each email to its parent email (used for grouping)

    def find(self, x):
        if x != self.parent.setdefault(x, x):  # If x not in parent, set parent[x] = x
            self.parent[x] = self.find(self.parent[x])  # Path compression
        return self.parent[x]

    def union(self, x, y):
        self.parent[self.find(x)] = self.find(y)  # Union x and y by setting root of x to root of y

class Solution:
    def accountsMerge(self, accounts: List[List[str]]) -> List[List[str]]:
        uf = UnionFind()
        email_to_name = {}  # Maps each email to the account holder's name

        # Step 1: Union emails within the same account
        for account in accounts:
            name = account[0]
            first_email = account[1]

            for email in account[1:]:
                uf.union(first_email, email)  # Union all emails in this account
                email_to_name[email] = name  # Track the name for each email

        # Step 2: Group emails by their root parent
        roots = defaultdict(list)  # Maps root email to all emails in its connected component
        for email in email_to_name:
            root = uf.find(email)
            roots[root].append(email)

        # Step 3: Format final merged account list
        result = []
        for root, emails in roots.items():
            name = email_to_name[root]  # Get name from any email in the group (they all belong to same person)
            result.append([name] + sorted(emails))

        return result

```

You are given a list of accounts. Each account contains a name and a list of emails. If two accounts have **at least one email in common**, they belong to the **same person**, and we should **merge** them.

Return the merged account list. The result should include:

*   Account name

*   A sorted list of unique emails

***

### 🧠 **Approach Using Union-Find**

*   Treat each **email** as a node.

*   If two emails are in the same account, union them.

*   Use a `parent` map to connect each email to its root.

*   Use a `name` map to track the name associated with each email.

### Summary of the dictionaries:

*   `self.parent`: Keeps track of connected components (email → parent email)

*   `email_to_name`: Maps each email to the account holder's name

*   `roots`: Groups all emails by their connected root (used to generate the final merged result)

### 🧠 Logic Summary

*   **Union-Find handles grouping** of emails efficiently.

*   Emails with the same root belong to the same person.

*   Final step is just formatting and sorting each group.

***

### ⏱️ Time and Space Complexity

*   **Time:** `O(N * α(N))`, where N is the number of emails and `α` is the inverse Ackermann function (very small). Sorting each group takes additional time.

*   **Space:** `O(N)` for storing parent mapping, email-to-name, and grouped roots.

Let me know if you want to visualize this with a real example!
