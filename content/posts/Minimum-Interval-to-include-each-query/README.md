---
id: 1807e332-de10-80c2-9a9e-c676df68294b
title: Minimum Interval to include each query
created_time: 2025-01-19T18:07:00.000Z
last_edited_time: 2025-10-15T18:10:00.000Z
difficulty_level: Hard
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: >-
  https://leetcode.com/problems/minimum-interval-to-include-each-query/description/
my_confidence_level: Low
last_solved: null
concept_involved:
  - Intervals
companies_asked:
  - Google
problem_name: Minimum Interval to include each query

---

```python
class Solution:
    def minInterval(self, intervals: List[List[int]], queries: List[int]) -> List[int]:
       intervals.sort()

       res, i, minHeap  = {}, 0, []

       for q in sorted(queries):

            while i < len(intervals) and intervals[i][0] <= q: 
                l, r = intervals[i]
                heapq.heappush(minHeap, (r-l + 1, r)) 
                i += 1
            
            while minHeap and minHeap[0][1] < q:
                heapq.heappop(minHeap)
            res[q] = minHeap[0][0] if minHeap else -1

       return [res[q] for q in queries]
```

**Java Code:**

```java
import java.util.*;

class Solution {
    public int[] minInterval(int[][] intervals, int[] queries) {
        Arrays.sort(intervals, Comparator.comparingInt(a -> a[0]));

        int n = queries.length;
        int[] result = new int[n];

        // Map each query to its original index
        int[][] sortedQueries = new int[n][2];
        for (int i = 0; i < n; i++) {
            sortedQueries[i][0] = queries[i];
            sortedQueries[i][1] = i;
        }
        Arrays.sort(sortedQueries, Comparator.comparingInt(a -> a[0]));

        // Min-heap of [interval size, end]
        PriorityQueue<int[]> minHeap = new PriorityQueue<>((a, b) -> a[0] - b[0]);

        int i = 0;
        for (int[] query : sortedQueries) {
            int q = query[0];
            int idx = query[1];

            while (i < intervals.length && intervals[i][0] <= q) {
                int l = intervals[i][0], r = intervals[i][1];
                minHeap.offer(new int[]{r - l + 1, r});
                i++;
            }

            while (!minHeap.isEmpty() && minHeap.peek()[1] < q) {
                minHeap.poll();
            }

            result[idx] = minHeap.isEmpty() ? -1 : minHeap.peek()[0];
        }

        return result;
    }
}

```

### **Minimum Interval to Include Each Query**

You are given a **2D list** **`intervals`**, where each `intervals[i] = [start_i, end_i]` represents an interval.

You are also given a **list of integers** **`queries`**.

For each query `q`, find the **length of the smallest interval** `[start, end]` such that:

*   `start <= q <= end`

*   If no such interval exists for the query, return `1`.

Time Complexity: O(nlogn + qlogq)

Space Complexity:  O(n + 1)

### **Space Complexity**:

*   Heap size can grow up to **n** in worst case (all intervals can sit in heap).

*   Result dictionary takes **q** space.

*   So total space is **O(n + q)**.

But if interviewer asks roughly, you can just say:

**Space Complexity = O(n + q)**.
