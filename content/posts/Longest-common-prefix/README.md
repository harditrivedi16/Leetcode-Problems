---
id: 2787e332-de10-80e8-a963-e8cc15efd0fc
title: Longest common prefix
created_time: 2025-09-24T14:48:00.000Z
last_edited_time: 2025-09-24T14:50:00.000Z
difficulty_level: Easy
number: 17
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode 250
problem_link: https://leetcode.com/problems/longest-common-prefix/description/
my_confidence_level: Meduim
last_solved: 2025-09-24T00:00:00.000Z
concept_involved:
  - Arrays
companies_asked:
  - Google
  - Amazon
  - Microsoft
  - Bloomberg
  - Facebook/Meta
  - Apple
  - IBM
  - Adobe
  - TicTok
problem_name: Longest common prefix

---

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

## Approach 1: Horizontal Scanning

### **Intuition**

*   Start with the first string as the prefix.

*   Compare it with each subsequent string.

*   While the string doesn’t start with the prefix, chop off the last character of the prefix.

*   Continue until all strings share the prefix, or prefix becomes empty.

### **Code**

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ""

        prefix = strs[0]
        for word in strs[1:]:
            while not word.startswith(prefix):
                prefix = prefix[:-1]
                if not prefix:
                    return ""
        return prefix


```

### **Complexity**

*   **Time:** O(N · M)

    *   N = number of strings, M = length of the shortest string

    *   Worst case: we check every character across all strings.

*   **Space:** O(1)

    *   Only using the prefix variable (no extra structures).

***

## 🔹 Approach 2: Sorting Trick

### **Intuition**

*   When the array is sorted, the smallest and largest strings (lexicographically) will differ the most.

*   The longest common prefix must be shared by these two extremes.

*   So, just compare the first and last string.

### **Code**

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ""

        strs.sort()
        first, last = strs[0], strs[-1]

        i = 0
        while i < len(first) and i < len(last) and first[i] == last[i]:
            i += 1
        return first[:i]


```

### **Complexity**

*   **Time:** O(N log N + M)

    *   Sorting costs O(N log N), comparing first and last costs O(M).

*   **Space:** O(1) (if in-place sort is allowed).

***

👉 **Which to use in an interview?**

*   **Horizontal scanning** → best balance of simplicity + efficiency.

*   **Sorting trick** → elegant, but slightly worse time complexity due to sorting.
