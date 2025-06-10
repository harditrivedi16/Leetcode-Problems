---
id: 1e07e332-de10-8052-bb08-c26933bc89e4
title: Car Fleet
created_time: 2025-04-25T13:51:00.000Z
last_edited_time: 2025-05-01T14:42:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Low
number: 32
june_interviews_prep: null
last_solved: null
concept_involved:
  - Stack
companies_asked: []
problem_name: Car Fleet

---

**Problem Statement:**

You are given `n` cars traveling towards the same destination.

Each car has a `position[i]` and a `speed[i]`.

A **car fleet** forms when a car catches up to another and moves together without passing.

Return the **number of car fleets** that reach the destination.

***

**Intuition:**

*   Calculate **time** for each car to reach the destination: `(target - position) / speed`.

*   **Sort cars** by starting position in descending order (closest to destination first).

*   As you iterate:

    *   If a car behind takes **more time** than the car ahead, it cannot catch up — new fleet.

    *   If it takes **less or equal time**, it merges into the fleet ahead.

*   Use a **stack** to track fleets by their arrival times.

***

**Code:**

```python
python
CopyEdit
def carFleet(target, position, speed):
    pairs = sorted(zip(position, speed), reverse=True)
    stack = []

    for pos, spd in pairs:
        time = (target - pos) / spd
        if not stack or time > stack[-1]:
            stack.append(time)
    return len(stack)


```

***

**Time Complexity:**

*   Sorting: `O(n log n)`

*   One pass: `O(n)`

*   ➔ **Overall: O(n log n)**

**Space Complexity:**

*   Stack storage: **O(n)** in worst case.
