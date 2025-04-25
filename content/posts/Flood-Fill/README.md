---
id: 1767e332-de10-8040-b91f-fd5aed3824da
title: Flood Fill
created_time: 2025-01-09T01:16:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: Easy
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/flood-fill/submissions/1510910192/
my_confidence_level: Meduim
number: 50
amazon_prep: 'No'
last_solved: 2025-01-16T00:00:00.000Z
concept_involved:
  - DFS
  - Graphs
  - BFS
companies_asked:
  - Amazon
  - Microsoft
  - Google
problem_name: Flood Fill

---

```python
from collections import deque
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        


        if not image: 
            return None
        

        rows, cols = len(image), len(image[0])
        visit = set()
        visited = [[False for _ in range(cols)] for _ in range(rows)]

        def dfs(r,c,originalColor): 
            
            if r < 0 or c < 0 or r >= rows or c >= cols or image[r][c] != originalColor or visited[r][c]: 
                return
            visited[r][c] = True
            
            image[r][c] = color

            dfs(r +1 , c, originalColor)
            dfs(r - 1, c, originalColor)
            dfs(r, c+1, originalColor)
            dfs(r, c-1, originalColor)

        def bfs(r,c,originalColor): 
            q = deque()
            q.append((r,c))
            visit.add((r,c))

            #originalColor = image[r][c]
            image[r][c] = color

            while q: 
                row, col = q.popleft()
                directions = [[1,0], [-1,0], [0,1], [0,-1]]

                for dr,dc in directions: 
                    r = row + dr
                    c = col + dc

                    if (r in range(rows) and 
                       c in range(cols) and
                       image[r][c] == originalColor and
                       (r,c) not in visit): 

                       image[r][c] = color
                       q.append((r,c))
                       visit.add((r,c))

        if sr in range(rows) and sc in range(cols): 
            originalColor = image[sr][sc]
            dfs(sr, sc, originalColor)
            #bfs(sr, sc, originalColor)
        
        return image


```

### **Time Complexity**

Both **BFS** and **DFS**: **O(M × N)**, where **M** and **N** are grid dimensions.

Each cell is visited once, making work proportional to grid size.

***

### **Space Complexity**

**DFS**: **O(M × N)** worst case due to recursion stack depth.

**BFS**: **O(min(M, N))** average, **O(M × N)** worst case due to queue size.
