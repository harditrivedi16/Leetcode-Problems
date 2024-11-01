# Valid Anagram

Companies asked : Adobe, Amazon, Apple, Bloomberg, Goldman Sachs, Google, JPMorgan, Microsoft, Uber, Yandex
Concept involved: Strings
Difficulty level: Easy
Last Solved : June 12, 2024
Leetcode Problem List: Blind 75, Neetcode - 150, Top Interview Questions
My Confidence Level : Meduim
Number: 2
Problem Link: https://leetcode.com/problems/valid-anagram/description/

## Given two strings `s` and `t`, return `true` *if* `t` *is an anagram of* `s`*, and* `false` *otherwise*. 
An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### Collections.Counter () Approach:

The `collections` library in Python is a built-in module that provides alternatives to Python’s general-purpose built-in containers, like dictionaries, lists, sets, and tuples. It includes specialized container datatypes that are designed to provide additional functionality or optimizations over the standard types.

`Counter` is a subclass of dictionary provided by the `collections` module. It is specifically designed to count hashable objects. It's an unordered collection where elements are stored as dictionary keys and their counts are stored as dictionary values.

```python
class Solution: 
	def validAnagram(self, s: List[char],t: List[char])-> bool: 
		return collections.Counter(s)==collections.Counter(t) 
```

**Explanation:** This solution uses Python's **`collections.Counter`** to count the frequency of each character in strings **`s`** and **`t`**, returning **`True`** if the frequency distributions are identical, indicating they are anagrams.

**Time Compelxity: O(a + b)** - The time complexity indeed becomes O(a + b) because the **`collections.Counter`** needs to traverse through each string completely to count the occurrences of each character. Here, **`a`** is the length of string **`s`** and **`b`** is the length of string **`t`**.

**Space Complexity: O(a + b)** - The space complexity depends on the number of distinct characters in both strings **`s`** and **`t`**