---
id: 14f7e332-de10-80e6-b279-f183d95ea8b5
title: LRU cache
created_time: 2024-12-01T18:11:00.000Z
last_edited_time: 2025-05-01T14:48:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
  - Top Interview Questions
  - Top 100 Liked Questions
  - Top Amazon Questions
  - Top Microsoft Questions
problem_link: https://leetcode.com/problems/lru-cache/description/
my_confidence_level: Low
last_solved: 2024-12-01T00:00:00.000Z
concept_involved:
  - Linked List
  - HashTables
companies_asked:
  - Amazon
  - Microsoft
  - Bloomberg
  - Facebook/Meta
  - Oracle
  - TicTok
  - Google
  - Apple
  - Uber
problem_name: LRU cache

---

```python
class Node: 
    def __init__(self, key, val): 
        self.key, self.val = key, val 
        self.prev = self.next = None

class LRUCache:

    def __init__(self, capacity: int):
        self.cap = capacity
        self.cache = {}

        self.left, self.right = Node(0,0), Node(0,0)
        self.left.next, self.right.prev = self.right, self.left
    
    #remove that node
    def remove(self, node): 
        prv, nxt = node.prev, node.next
        prv.next, nxt.prev = nxt, prv

    #insert the element at the right most node
    def insert(self,node): 
        prv, nxt = self.right.prev, self.right
        prv.next = nxt.prv= node
        node.prev, node.next= prv, nxt
        

    def get(self, key: int) -> int:
        if key in self.cache: 
            self.remove(self.cache[key])
            self.insert(self.cache[key])
            return self.cache[key].val 
        return -1
    
        

    def put(self, key: int, value: int) -> None:
        if key in self.cache: 
            self.remove(self.cache[key])
        self.cache[key] = Node(key,value)
        self.insert(self.cache[key])

        if len(self.cache) > self.cap: 
            lru = self.left.next
            self.remove(lru)
            del self.cache[lru.key]

       


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```

Time Complexity: O(1) for each get and put function

Space Complexity= O(n) as we created a hashmap
