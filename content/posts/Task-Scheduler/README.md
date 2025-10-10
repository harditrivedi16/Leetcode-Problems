---
id: 1d57e332-de10-80d6-8454-d4234cd44095
title: Task Scheduler
created_time: 2025-04-14T18:02:00.000Z
last_edited_time: 2025-05-01T15:43:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/task-scheduler/description/
my_confidence_level: Low
last_solved: 2025-04-14T00:00:00.000Z
concept_involved:
  - heaps
  - HashTables
companies_asked:
  - Roblox
  - Amazon
  - Google
  - Apple
  - Snowflake
problem_name: Task Scheduler

---

```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:

        count = collections.Counter(tasks)
        maxHeap = [-cnt for cnt in count.values()]
        heapq.heapify(maxHeap)
        time = 0 
        q = deque() # [cnt, idletime]

        while maxHeap or q: 
            time += 1

            if maxHeap: 
                cnt = 1 + heapq.heappop(maxHeap)
                if cnt < 0: 
                    q.append([cnt,time + n])
            
            if q and q[0][1] == time: 
                heapq.heappush(maxHeap,q.popleft()[0])
        
        return time


        
```

### 🔍 Key Insight:

To reduce idle time:

*   Focus on the **task that appears the most** (say, 'A' appears 3 times).

*   Spread its appearances with `n` time in between.

*   Fit other tasks or idle spaces in between.

***

### 🧠 Analogy:

Imagine 'A' is the most frequent task:

```plain text
css
CopyEdit
A _ _ A _ _ A


```

Here, `_` are either **idle** or **other tasks**. You’re trying to **fill these blanks** so you don’t waste time.

If you can place other tasks in those gaps, you reduce the total time. If not, you fill it with idles.

Time Complexity= O (n) technically O(n + idle time)

Space Complexity= O(1)
