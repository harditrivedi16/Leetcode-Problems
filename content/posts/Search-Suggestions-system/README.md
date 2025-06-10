---
id: 1e27e332-de10-8046-a619-ed30b092b3b3
title: Search Suggestions system
created_time: 2025-04-27T17:44:00.000Z
last_edited_time: 2025-05-01T14:31:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 17
june_interviews_prep: null
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Binary Search
companies_asked: []
problem_name: Search Suggestions system

---

```python
python
CopyEdit
import bisect

def suggestedProducts(products, searchWord):
    # Step 1: Sort the products lexicographically
    products.sort()

    result = []
    prefix = ""

    # Step 2: For each character in searchWord, generate the prefix and find matching products
    for char in searchWord:
        prefix += char

        # Step 3: Use binary search to find the position where the prefix could be inserted
        index = bisect.bisect_left(products, prefix)

        # Step 4: Collect the top 3 lexicographically smallest products that match the prefix
        suggestions = []
        for i in range(index, min(index + 3, len(products))):
            if products[i].startswith(prefix):
                suggestions.append(products[i])

        result.append(suggestions)

    return result


```

### Approach:

*   **Sort the Products:**

    Start by sorting the list of products lexicographically. This will allow us to efficiently find products that match any given prefix.

*   **Prefix Matching:**

    For each character in the `searchWord`, we generate the prefix of the search word and look for all products that start with this prefix.

*   **Efficient Search with Binary Search:**

    To find products that match the current prefix efficiently, use **binary search**. The `bisect_left` function from the `bisect` module can be used to find the index of the first product that starts with the prefix.

*   **Collect Matches:**

    After finding the starting index of products that match the prefix, iterate over the list and collect up to the next three products to match the requirement of returning the **top 3 lexicographically smallest** products.

### Code:

### Explanation:

*   **Sorting the products**:

    The products list is sorted lexicographically at the beginning. This ensures that we can find matching products efficiently using binary search.

*   **Binary Search for Prefix Matching**:

    For each prefix in the search word, we use `bisect_left` to find the position where this prefix would fit in the sorted list. This helps in narrowing down the matching products quickly.

*   **Collecting the Top 3 Matches**:

    After finding the index, we iterate through the next 3 products and check if they match the current prefix. These are the top 3 lexicographically smallest matching products.

*   **Return the Results**:

    For each prefix of the search word, we append the list of top 3 matching products to the result.

### Time Complexity:

*   **Sorting** the products takes `O(n log n)`, where `n` is the number of products.

*   For each character in the `searchWord` (which is of length `m`), we perform a binary search with `bisect_left`, which takes `O(log n)`. After that, we potentially check the next 3 products, so the time for each query is `O(3)`, which is a constant.

*   Therefore, for each character in the search word, the overall time complexity is `O(log n)`.

So the total time complexity is:

*   **Sorting the products**: `O(n log n)`

*   **For each query**: `O(m log n)`

Thus, the overall time complexity is:

*   **Time Complexity**: `O(n log n + m log n)`

Where:

*   `n` is the number of products.

*   `m` is the length of the searchWord.

### Space Complexity:

*   The space complexity is primarily for storing the sorted list of products and the result list:

    *   **Result list**: `O(m)` where `m` is the length of the searchWord (because for each prefix, we store up to 3 products).

    *   **Sorting**: We use `O(n)` space for the sorted list of products.

Thus, the **space complexity** is:

*   **Space Complexity**: `O(n + m)`

### Edge Cases:

*   If no products match a given prefix, the output will be an empty list for that prefix.

*   If all products match the prefix, the output will contain all the matching products (up to 3).

*   If the `searchWord` is empty, the function should return an empty list for each prefix.
