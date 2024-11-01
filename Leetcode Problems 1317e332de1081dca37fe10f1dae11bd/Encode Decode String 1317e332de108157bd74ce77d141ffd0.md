# Encode Decode String

Companies asked : Cisco, Facebook/Meta, Google, Microsoft, Snowflake
Concept involved: Arrays, Strings
Difficulty level: Meduim 
Last Solved : October 3, 2024
Leetcode Problem List: Blind 75, Leetcode Curated Algorithms, Neetcode - 150
My Confidence Level : Low
Number: 13
Problem Link: https://leetcode.com/problems/encode-and-decode-strings/description/

## Problem

Design an algorithm to encode **a list of strings** to **a string**. The encoded string is then sent over the network and is decoded back to the original list of strings.

Machine 1 (sender) has the function:

```
string encode(vector<string> strs) {
  // ... your code
  return encoded_string;
}
```

Machine 2 (receiver) has the function:

```
vector<string> decode(string s) {
  //... your code
  return strs;
}

```

So Machine 1 does:

```
string encoded_string = encode(strs);

```

and Machine 2 does:

```
vector<string> strs2 = decode(encoded_string);

```

`strs2` in Machine 2 should be the same as `strs` in Machine 1.

Implement the `encode` and `decode` methods.

You are not allowed to solve the problem using any serialize methods (such as `eval`).

**Example 1:**

```
Input: dummy_input = ["Hello","World"]
Output: ["Hello","World"]
Explanation:
Machine 1:
Codec encoder = new Codec();
String msg = encoder.encode(strs);
Machine 1 ---msg---> Machine 2

Machine 2:
Codec decoder = new Codec();
String[] strs = decoder.decode(msg);
```

## Solution

```python
class Solution:
    def encode(self, strs):
        """
        Encodes a list of strings to a single string.
        
        @param strs: A list of strings
        @return: Encoded single string
        """
        res = ""
        for s in strs:
            res += str(len(s)) + "#" + s
        return res

    def decode(self, str):
        """
        Decodes a single string to a list of strings.
        
        @param str: A string
        @return: Decoded list of strings
        """
        res, i = [], 0
        while i < len(str):
            j = i
            while str[j] != "#":
                j += 1
            length = int(str[i:j])
            res.append(str[j + 1: j + 1 + length])
            i = j + 1 + length
        return res

```

### Core Idea Behind the Solution (4 Lines)

1. Encode a list of strings into a single string that contains the length of each string followed by a delimiter and the string itself.
2. Decode the single string back into the original list of strings by parsing the length and extracting the corresponding substrings.
3. Use a specific delimiter (`#`) to separate the length of the string from the string itself in the encoded format.
4. Ensure the encoding and decoding processes are reversible and handle all edge cases, including empty strings.

### Explanation of Encode Function (2 Lines)

The `encode` function concatenates the length of each string, a delimiter (`#`), and the string itself, building a single encoded string from a list of strings. This allows each string to be decoded later by knowing the length and using the delimiter.

### Explanation of Decode Function (2 Lines)

The `decode` function reads the length of each string by parsing up to the delimiter (`#`), then extracts the string based on the length, repeating until the entire encoded string is processed, reconstructing the original list of strings.

### Time Complexity and Space Complexity (2 Lines)

- **Time Complexity**: `O(N)`, where `N` is the total number of characters in all strings combined, as each character is processed once during encoding and decoding.
- **Space Complexity**: `O(N)`, as additional space is used to store the encoded string and the decoded list of strings, both of which are proportional to the input size.