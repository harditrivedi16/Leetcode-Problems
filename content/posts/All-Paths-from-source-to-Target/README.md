---
id: 1767e332-de10-803c-8e9a-f894c3c65c72
title: All Paths from source to Target
created_time: 2025-01-09T01:16:00.000Z
last_edited_time: 2025-04-24T16:49:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/all-paths-from-source-to-target/description/
my_confidence_level: Meduim
number: 53
amazon_prep: 'No'
last_solved: 2025-01-16T00:00:00.000Z
concept_involved:
  - BFS
  - Graphs
  - DFS
companies_asked:
  - Bloomberg
problem_name: All Paths from source to Target

---

```python
class Solution:
    def allPathsSourceTarget(self, graph: List[List[int]]) -> List[List[int]]:
        
        #BFS Approach
        target= len(graph) - 1
        # Initialize a queue as list of lists and add [0] as it's element
        queue = deque([[0]]) 
        result = []

        while queue: 

            path = queue.popleft()# pops the first element
            node = path[-1]

            if node == target: 
                result.append(path)
            
            for i in graph[node]: 
                new_path = path + [i]
                queue.append(new_path)
        return result
        

## DFS Approach 
'''
        target = len(graph) - 1
        result = [] 
        def dfs(path: List[int]):
            # Get the current node (last element in the path)
            node = path[-1]

            # If we've reached the target node, add the path to the result
            if node == target: 
                result.append(path)
                return 

            # Explore each neighbor of the current node
            for neighbor in graph[node]: 
                # Recursively call dfs with the new path including the neighbor
                dfs(path + [neighbor])

        # Start DFS from the source node (0)
        dfs([0])

        # Return all paths found from source to target
        return result
        '''
```

Time Complexity: O(no of paths \* length of each path + total no. of edges )

Space complexity: O(no of paths  \* length of each paths)
