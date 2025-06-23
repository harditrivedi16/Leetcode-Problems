---
id: 2197e332-de10-80b6-be9e-e022884431df
title: Hand of Straights
created_time: 2025-06-21T19:46:00.000Z
last_edited_time: 2025-06-22T14:29:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: null
june_interviews_prep: null
last_solved: 2025-06-21T00:00:00.000Z
concept_involved:
  - Greedy
companies_asked: []
problem_name: Hand of Straights

---

**Problem Statement:**

You're given an integer array `hand` representing cards, and an integer `groupSize`.

Return `True` if the hand can be rearranged into groups of `groupSize` **consecutive cards**, else `False`.

**Example:**

```python
python
CopyEdit
hand = [1,2,3,6,2,3,4,7,8], groupSize = 3
✅ Output: True → can be rearranged into [1,2,3], [2,3,4], [6,7,8]


```

```python
class Solution:
    def isNStraightHand(self, hand, groupSize):
        if len(hand) % groupSize:
            return False

        count = Counter(hand)
        hand.sort()
        for num in hand:
            if count[num]:
                for i in range(num, num + groupSize):
                    if not count[i]:
                        return False
                    count[i] -= 1
        return True
```
