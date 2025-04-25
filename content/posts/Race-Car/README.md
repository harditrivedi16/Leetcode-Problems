---
id: 1df7e332-de10-80f3-b94c-e72b0751d140
title: Race Car
created_time: 2025-04-24T16:24:00.000Z
last_edited_time: 2025-04-24T16:46:00.000Z
difficulty_level: Hard
remarks: Complicated BFS Traversal
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: >-
  https://leetcode.com/problems/race-car/description/?envType=problem-list-v2&envId=7p5x763
my_confidence_level: Meduim
number: 128
amazon_prep: 'Yes'
last_solved: 2025-04-24T00:00:00.000Z
concept_involved:
  - Graphs
companies_asked:
  - Amazon
problem_name: Race Car

---

```python
class Solution:
    def racecar(self, target: int) -> int:
        queue = deque([(0, 1)])  # Start at position 0 with speed +1
        visited = set((0, 1))
        steps = 0  # Count number of instructions
        
        while queue:
            for _ in range(len(queue)):
                pos, speed = queue.popleft()
                
                # If we reach the target position
                if pos == target:
                    return steps
                
                # Instruction A: Accelerate
                next_pos = pos + speed
                next_speed = speed * 2
                next_state = (next_pos, next_speed)
                
                # Limit the bounds to avoid unnecessary exploration
                if 0 <= next_pos <= 2 * target and next_state not in visited:
                    visited.add(next_state)
                    queue.append(next_state)

                # Instruction R: Reverse (change direction)
                rev_speed = -1 if speed > 0 else 1
                rev_state = (pos, rev_speed)
                if rev_state not in visited:
                    visited.add(rev_state)
                    queue.append(rev_state)
            
            steps += 1  # Increment step after exploring all current states

        return -1
        
```

Complicated BFS Traversal Problem
🔄 At Every Node (State):
You stand at a position pos with a speed speed.

You have 2 options:

Accelerate ("A")

Move to pos + speed

Update speed to speed \* 2

Reverse ("R")

Stay at pos

Change speed to +1 if speed < 0, or -1 if speed > 0

These two transitions give us 2 new nodes (states).

🔍 Then What?
For each new state, we check if pos == target

If yes → we return the number of instructions taken so far (i.e., the depth of that node in BFS).

If no → add the state to the queue (only if it's not visited before), and continue exploring.

Why 2 \* target is a good cap:
It allows enough space for overshooting and correcting.

Ensures we never ignore optimal paths, but avoid infinite unnecessary states.

Empirically and mathematically, no optimal sequence will ever require you to go further than 2 \* target. If it does, there's already a shorter way.

Time complexity: Ist iteration we see 2 states, next we see 4 states and then 8 and so on so target^2. but we will not reach there at all as since we are keeping visited states.

Space complexity: same as time complexity.
