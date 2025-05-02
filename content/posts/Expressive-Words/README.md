---
id: 1e27e332-de10-80f6-9d97-e0cc92253dbe
title: Expressive Words
created_time: 2025-04-27T18:33:00.000Z
last_edited_time: 2025-05-01T15:34:00.000Z
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: null
my_confidence_level: Meduim
number: 77
amazon_prep: 'Yes'
last_solved: 2025-04-27T00:00:00.000Z
concept_involved:
  - Two Pointers
  - Strings
companies_asked: []
problem_name: Expressive Words

---

```python
class Solution:
    def expressiveWords(self, words: List[str], s: str) -> int:
        # Helper function to check if a single word is expressive in string `s`
        def isExpressive(word, s):
            i, j = 0, 0  # i is for the string `s`, j is for the `word`
            
            # Traverse through the string `s` and the current `word`
            while i < len(s) and j < len(word):
                if s[i] == word[j]:
                    # If characters match, count how many consecutive characters there are in both `s` and `word`
                    count_s, count_word = 1, 1
                    
                    # Count consecutive characters in `s` (same as current `s[i]`)
                    while i + 1 < len(s) and s[i] == s[i + 1]:
                        count_s += 1
                        i += 1
                    
                    # Count consecutive characters in `word` (same as current `word[j]`)
                    while j + 1 < len(word) and word[j] == word[j + 1]:
                        count_word += 1
                        j += 1
                    
                    # The word is expressive if:
                    # 1. The number of characters in `s` must be at least as many as in `word` (count_s >= count_word)
                    # 2. If `count_s > count_word`, we need at least 3 consecutive characters in `s` to stretch it (count_s >= 3)
                    if count_s < count_word or (count_s > count_word and count_s < 3):
                        return False
                    
                    # Move both pointers (i for `s`, j for `word`)
                    i += 1
                    j += 1
                else:
                    # If characters do not match, just move `i` forward to try the next character in `s`
                    i += 1
            
            # After the loop, `j` should have processed all characters in `word`
            return j == len(word)
        
        result = 0  # To store the count of expressive words
        
        # Iterate over each word in the `words` list and check if it is expressive in `s`
        for word in words:
            if isExpressive(word, s):
                result += 1
        
        # Return the total count of expressive words
        return result

```

*   **isExpressive function**:

    *   It checks if a word is expressive by comparing it character by character with the string `s`.

    *   It counts how many consecutive characters are the same in both `s` and the `word`.

    *   If there are more consecutive characters in `s` (and at least 3 of them), the word can be stretched. If there are fewer, or if it doesn't match, it returns `False`.

*   **Main loop**:

    *   For each word in the `words` list, it calls the `isExpressive` function to check if the word can be formed from `s` by deleting some characters and possibly stretching others.

*   **Return**:

    *   The function returns the total number of expressive words from the list `words`.

### Time and Space Complexity:

*   **Time Complexity**: O(n \* m), where `n` is the number of words in the `words` list, and `m` is the average length of each word. This is because for each word, we are scanning the string `s` to check for expressiveness.

*   **Space Complexity**: O(1), as we are not using any extra space proportional to the input size. The only additional space is for the `count_s` and `count_word` counters, which are fixed.
