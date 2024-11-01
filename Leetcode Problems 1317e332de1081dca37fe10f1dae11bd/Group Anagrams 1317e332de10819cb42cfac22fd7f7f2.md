# Group Anagrams

Companies asked : Adobe, Amazon, Apple, Bloomberg, Facebook/Meta, Goldman Sachs, Google, Microsoft, Nvidia, Oracle, Ripple, Salesforce, ServiceNow, TicTok, Visa, Yahoo, Yandex, Zoho
Concept involved: HashTables, Strings
Difficulty level: Meduim 
Last Solved : April 21, 2024
Leetcode Problem List: Blind 75, Neetcode - 150, Top 100 Liked Questions, Top Amazon Questions, Top Interview Questions
My Confidence Level : Meduim
Number: 6
Problem Link: https://leetcode.com/problems/group-anagrams/description/

## Group Anagrams

### Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### Explanation: Hashmap Approach

In the **`groupAnagrams`** function you provided, a tuple is used as a key in a dictionary to store anagrams grouped together based on their character counts. Here’s a step-by-step breakdown of why and how this is done:

1. **Character Count Array**: For each string in the input list **`strs`**, a count array of size 26 is created, where each index represents a letter from 'a' to 'z'. The array stores the frequency of each character in the string. This is done by iterating over each character **`c`** in the string **`s`**, and incrementing the respective index in the count array (**`count[ord(c)- ord('a')]`**).
2. **Using Tuple as Key**: Once the count array for a string is populated, it is converted to a tuple (**`tuple(count)`**). This conversion is essential because lists (like **`count`**) cannot be used as dictionary keys since they are mutable (changeable). Tuples, on the other hand, are immutable (unchangeable) and can be used as keys in a dictionary. This tuple acts as a unique identifier for each group of anagrams; any string that results in the same tuple of character counts is an anagram of the others in the group.
3. **Grouping in Dictionary**: The **`defaultdict(list)`** is used to create a dictionary where each key is a tuple (as described above) and the value is a list of strings that are anagrams of each other (i.e., strings that have the same character count tuple). Each string **`s`** is appended to the list in the dictionary corresponding to its character count tuple.
4. **Returning Groups**: The method **`ans.values()`** is called at the end of the function. This returns a view object that displays all the values of the dictionary. In this context, each value is a list of anagrams, so **`ans.values()`** returns all the groups of anagrams. Since a dictionary view is not a list, but an iterable that displays the values, you might see it commonly converted to a list for practical usage, e.g., **`list(ans.values())`**, depending on the context in which the function is used.

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ans = defaultdict(list)

        for s in strs: 
            count = [0] * 26

            for c in s: 
                count[ord(c)- ord('a')] += 1
            t = tuple(count)

            ans[t].append(s)

        return ans.values()
```

- Time Complexity: O(NK)O(NK)*O*(*NK*), where NN*N* is the length of `strs`, and KK*K* is the maximum length of a string in `strs`. Counting each string is linear in the size of the string, and we count every string.
- Space Complexity: O(NK)O(NK)*O*(*NK*), the total information content stored in `ans`.