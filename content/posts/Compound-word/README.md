---
id: 1e47e332-de10-803e-991f-e1763f7f327d
title: Compound word
created_time: 2025-04-29T17:31:00.000Z
last_edited_time: 2025-05-01T15:21:00.000Z
difficulty_level: Hard
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list: []
problem_link: not on leetcode
my_confidence_level: Low
last_solved: 2025-04-29T00:00:00.000Z
concept_involved:
  - HashTables
  - Arrays
companies_asked:
  - Amazon
problem_name: Compound word

---

You are given a (potentially large) list of words. Some of these are compound words, where all parts are also in the List.

Example Input:

\["rockstar", "rock", "star", "rocks", "tar", "rockstars", "super", "superhighway", "highway", "high", "way", "superhighway"]

Identify all combinations of words in the list which form a compound word also in the list. Return the set of unique combinations.

Example Compound: "highway" = ("high + "way")

Output Format: {"rockstar": \["rock", "star], "superhighway": \["super", "highway"]}

```python
class Solution: 
    def findList(words): 
      word_set = set(words)
      compounds = {}
      for word in words: 
        for ch range(1,len(word)):
          if word[:ch] in word_set and word[ch:] in word_set: 
            compound[word] =[ word[:ch], word[ch:]]
            break 
      return compounds
```

Time complexity: O(n\*m) n = len of words list, m = avg. len of each word

space complexity: O(n)
