---
id: 1e27e332-de10-80bf-ac06-d345b85fffa6
title: Copy List with a Random Pointer
created_time: 2025-04-27T20:35:00.000Z
last_edited_time: 2025-04-27T20:36:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 164
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Linked List
companies_asked: []
problem_name: Copy List with a Random Pointer

---

```python
class Node:
    def __init__(self, val=None, next=None, random=None):
        self.val = val
        self.next = next
        self.random = random

class Solution:
    def copyRandomList(self, head: 'Node') -> 'Node':
        if not head:
            return None
        
        # Step 1: Create a hashmap to store the mapping of original nodes to copied nodes
        old_to_new = {}
        
        current = head
        while current:
            # Create a copy of the node and store it in the hashmap
            old_to_new[current] = Node(current.val)
            current = current.next
        
        # Step 2: Set the next and random pointers for the new nodes
        current = head
        while current:
            # Set the next pointer of the copied node
            if current.next:
                old_to_new[current].next = old_to_new[current.next]
            # Set the random pointer of the copied node
            if current.random:
                old_to_new[current].random = old_to_new[current.random]
            current = current.next
        
        # Step 3: Return the head of the copied list
        return old_to_new[head]

```

### **Explanation:**

*   **Step 1 (Hashmap Creation):**

    We traverse the original list and for each node, we create a new node with the same value and store it in a hashmap `old_to_new`. The key in the hashmap is the original node, and the value is the newly created node.

*   **Step 2 (Setting Pointers):**

    We traverse the original list again, and for each node, we set the `next` and `random` pointers of the copied nodes using the hashmap. The `next` pointer is set by referring to the copied version of the `next` node, and the `random` pointer is set by referring to the copied version of the `random` node.

*   **Step 3 (Returning Result):**

    Finally, the head of the copied list is returned. Since we have stored all the mappings in the hashmap, we can easily access the head of the copied list using `old_to_new[head]`.

### **Time Complexity:**

*   **O(L):** We traverse the list twice: once to create the hashmap and once to set the `next` and `random` pointers. Thus, the time complexity is O(L), where L is the number of nodes in the list.

### **Space Complexity:**

*   **O(L):** We are using a hashmap to store a mapping from each original node to its copied node. Therefore, the space complexity is O(L), where L is the number of nodes in the list.

This approach also has a linear time complexity and space complexity but uses a hashmap to store the node mappings instead of modifying the list structure directly.
