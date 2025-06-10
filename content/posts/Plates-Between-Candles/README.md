---
id: 1e27e332-de10-80c2-a44c-f7452e948a6b
title: Plates Between Candles
created_time: 2025-04-27T17:23:00.000Z
last_edited_time: 2025-05-01T14:30:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 13
june_interviews_prep: null
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Plates Between Candles

---

```python
def platesBetweenCandles(s):
    n = len(s)
    
    # Create an array to store the number of plates up to each index
    plate_count = [0] * n
    count = 0
    
    # Fill the plate_count array
    for i in range(n):
        if s[i] == '*':
            count += 1
        plate_count[i] = count
    
    # Create the result array
    result = [0] * n
    # Initialize the position of the last candle
    last_candle = -1
    
    # Traverse the string to fill the result array
    for i in range(n):
        if s[i] == '|':
            last_candle = i
        elif s[i] == '*' and last_candle != -1:
            # If we find a plate and there's a candle before it, calculate the plates between them
            next_candle = last_candle
            for j in range(i+1, n):
                if s[j] == '|':
                    next_candle = j
                    break
            if next_candle != -1:
                result[i] = plate_count[next_candle] - plate_count[last_candle]
    
    return result

```

### **Explanation:**

*   **Plate Count Array**:

    First, we iterate through the string `s` and build a `plate_count` array where each index `i` stores the total number of plates from the start to index `i`. This helps us count the number of plates between two candles efficiently.

*   **Result Array**:

    We then traverse through the string again and for each `'*'` (plate) character, check if there is a candle (`'|'`) before it. For the found candle, calculate the number of plates between this plate and the next candle (using the `plate_count` array).

*   **Edge Handling**:

    We handle the edge case where there are no candles to the right of a plate by setting the result to `0`.

***

### **Time Complexity:**

*   **Building the plate count array**: `O(n)`

    We traverse the string once to fill the `plate_count` array.

*   **Calculating the result**: `O(n)`

    We traverse the string again to calculate the result.

Thus, the overall time complexity is **O(n)**, where `n` is the length of the string.

### **Space Complexity:**

*   **plate\_count and result arrays**: `O(n)`

    We use two additional arrays to store the plate counts and the result, each of size `n`.

Thus, the space complexity is **O(n)**.
