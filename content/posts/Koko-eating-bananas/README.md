---
id: 1e27e332-de10-80ec-9969-e84bf9bf274b
title: Koko eating bananas
created_time: 2025-04-27T16:25:00.000Z
last_edited_time: 2025-04-29T21:15:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Koko eating bananas

---

```python
import math

def minEatingSpeed(piles, h):
    left, right = 1, max(piles)
    result = right

    while left <= right:
        mid = (left + right) // 2
        hours = 0
        for pile in piles:
            hours += math.ceil(pile / mid)
        
        if hours <= h:
            result = mid
            right = mid - 1  # try slower speed
        else:
            left = mid + 1  # need faster speed

    return result

```

**Intuition:**

*   Higher eating speed (`k`) means Koko can finish faster.

*   Lower eating speed (`k`) means it takes longer.

*   So **eating speed** **`k`** and **hours needed** have an **inverse relationship**.

*   We can **binary search** the minimum `k` between `1` and `max(piles)`.

At each mid-speed `k`, simulate how many hours it would take:

*   For each pile, time = `ceil(pile / k)`.

*   Sum all times → if total time ≤ `h`, then `k` is valid (try smaller `k`).

*   Else, need a bigger `k`.

***

Exactly right, Hardi:

✅ **Time Complexity:** O(log(max(piles)) × n) — because for each guess of `k`, we scan all `n` piles.

✅ **Space Complexity:** O(1).
