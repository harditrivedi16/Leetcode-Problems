---
id: 1da7e332-de10-8092-b36a-de501da9ee57
title: Number of Connected Components in an Undirected Graph
created_time: 2025-04-19T19:29:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/
my_confidence_level: Low
last_solved: 2025-04-19T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Number of Connected Components in an Undirected Graph

---

```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        par = [i for i in range(n)]
        rank = [1] * n 

        def find(n1): 
            if n1 != par[n1]:
                par[n1] = find(par[n1])  # Full path compression
            return par[n1]
        
        def union(n1, n2): 
            p1, p2 = find(n1), find(n2)
            
            if p1 == p2: 
                return 0 
            
            if rank[p2] > rank[p1]: 
                par[p1] = p2
                rank[p2] += rank[p1]
            
            else: 
                par[p2] = p1
                rank[p1] += rank[p2]
            return 1
        
        res = n

        for n1, n2 in edges: 
            res -= union(n1,n2)
        
        return res



```

**Time Complexity:**

`O(α(n) * E)` — α is the inverse Ackermann function (almost constant); E = number of edges.

**Space Complexity:**

`O(n)` — for the parent array.

Let me know if you want to do the version with union by rank/size too.

4o

> 💡 Ackermann function: a function that is rapidly growning recursive function

    Inverse Ackermann function: a function that is slowly growing so it is considered as a constant. 

    Basically, 

    - To understand this, the **Ackermann function** involves repeated recursive calls with very large numbers. The inverse function (**α(n)**) is the number of times you need to recurse before you reach or exceed **n**, and this number increases extremely slowly.
