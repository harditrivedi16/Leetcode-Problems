---
id: 1e47e332-de10-80b6-b1f6-d3d4931a3b5c
title: Walls and Gates
created_time: 2025-04-29T19:20:00.000Z
last_edited_time: 2025-04-29T21:18:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked: []
problem_name: Walls and Gates

---

### Problem Statement:

You are given a 2D grid `rooms` where:

*   `1` represents a wall.

*   `0` represents a gate.

*   `INF` (represented by a large number like 2147483647) represents an empty room.

Fill each empty room with the distance to its nearest gate. If it is impossible to reach a gate, leave the room as `INF`.

### Approach:

To solve this problem efficiently, we can use **Breadth-First Search (BFS)**. The idea is to treat all the gates as starting points and propagate the distances to all the empty rooms using BFS. Since BFS explores nodes level by level, this ensures that we fill the rooms with the shortest distance to a gate.

### Steps:

*   **Initialize the BFS queue** with all the gates (cells with `0`).

*   **Propagate the distances** to the neighboring cells (rooms) from the gates. The distance of each neighboring room is the distance of the current room + 1.

*   **Stop** when all rooms have been processed, and the grid will have the correct distance to the nearest gate for all rooms.

### Code:

```python
python
CopyEdit
from collections import deque

class Solution:
    def wallsAndGates(self, rooms: List[List[int]]) -> None:
        if not rooms:
            return

        rows, cols = len(rooms), len(rooms[0])
        queue = deque()

        # Add all the gates to the BFS queue
        for r in range(rows):
            for c in range(cols):
                if rooms[r][c] == 0:  # Gate found
                    queue.append((r, c))

        # Directions for moving up, down, left, right
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]

        while queue:
            r, c = queue.popleft()
            # Explore all 4 neighbors
            for dr, dc in directions:
                nr, nc = r + dr, c + dc
                # Check if the neighbor is within bounds and is an empty room
                if 0 <= nr < rows and 0 <= nc < cols and rooms[nr][nc] == 2147483647:
                    # Set the distance to the nearest gate
                    rooms[nr][nc] = rooms[r][c] + 1
                    # Add the room to the queue to explore its neighbors
                    queue.append((nr, nc))


```

### Time Complexity:

*   **BFS traversal**: We process each cell in the grid once, and for each cell, we perform constant time operations (adding to the queue, checking neighbors).

*   Thus, the time complexity is **O(rows \* cols)**, where `rows` and `cols` are the dimensions of the grid.

### Space Complexity:

*   **BFS queue**: In the worst case, the queue will store all rooms, so the space complexity is **O(rows \* cols)**.

*   **Grid storage**: The grid is modified in place, so the space complexity for the grid itself is also **O(rows \* cols)**.

### Summary:

*   **Time Complexity**: O(rows \* cols)

*   **Space Complexity**: O(rows \* cols)
