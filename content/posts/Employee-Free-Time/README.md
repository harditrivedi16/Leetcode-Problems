---
id: 1dd7e332-de10-80b5-8675-cc9300b94a5d
title: Employee Free Time
created_time: 2025-04-22T18:21:00.000Z
last_edited_time: 2025-04-28T15:40:00.000Z
difficulty_level: Hard
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: https://leetcode.com/problems/employee-free-time/description/
my_confidence_level: Meduim
number: 126
amazon_prep: 'Yes'
last_solved: null
concept_involved:
  - Intervals
companies_asked: []
problem_name: Employee Free Time

---

### **Problem: Employee Free Time**

**Statement**

You are given a list `schedule`, where `schedule[i]` represents the working time of the `i-th` employee. Each employee has a list of non-overlapping intervals sorted by start time.

Return the list of **finite** free time intervals common to all employees.

Each interval should be represented as a list `[start, end]`.

### **Intuition:**

*   Treat all intervals together — flatten all employee schedules into one list.

*   Sort all intervals by **start time**.

*   Merge overlapping intervals, and whenever there’s a **gap** between two intervals, that gap is **free time**.

***

**Code:**

```python
python
CopyEdit
class Solution:
    def employeeFreeTime(self, schedule: List[List[List[int]]]) -> List[List[int]]:
        # Flatten all intervals
        intervals = [iv for employee in schedule for iv in employee]

        # Sort by start time
        intervals.sort(key=lambda x: x[0])

        res = []
        prev_end = intervals[0][1]

        for i in range(1, len(intervals)):
            if intervals[i][0] > prev_end:
                res.append([prev_end, intervals[i][0]])
            prev_end = max(prev_end, intervals[i][1])

        return res


```

***

### ⏱ **Time Complexity:**

*   Flattening all intervals = O(N)

*   Sorting intervals = O(N log N)

*   Scanning through intervals = O(N)

**Overall: O(N log N)**

(where N = total number of intervals)

***

### 🗃 **Space Complexity:**

*   O(N) to store all intervals and the result.
