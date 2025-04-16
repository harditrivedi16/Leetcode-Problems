---
id: 1d57e332-de10-80d6-8454-d4234cd44095
title: Task Scheduler
created_time: 2025-04-14T18:02:00.000Z
last_edited_time: 2025-04-15T15:59:00.000Z
difficulty_level: 'Meduim '
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/task-scheduler/description/
my_confidence_level: Low
number: 74
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

Time Complexity= O (n) technically O(n + idle time)

Space Complexity= O(1)
