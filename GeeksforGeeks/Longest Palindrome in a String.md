# Problem: Longest Palindrome in a String

Given a string S, find the longest palindromic substring in S.

## Example

Input: S = "aaaabbaa"
Output: aabbaa
Explanation: The longest palindromic substring is "aabbaa".

Input: S = "abc"
Output: a
Explanation: "a", "b", and "c" are the longest palindromes with the same length. The result is the one with the least starting index.

## Solution

```python
class Solution:
    def longestPalin(self, S):
        res = ""
        s2 = 0
        if S == S[::-1]:
            return S
        for i in range(len(S)):
            st = ""
            s1 = 0
            for j in range(i, len(S)):
                st += S[j]
                s1 += 1
                if st == st[::-1]:
                    if s1 > s2:
                        res = st
                        s2 = s1
        return res
```
## Approach

To find the longest palindromic substring in a string, we can iterate through all possible substrings and check if each substring is a palindrome. We can keep track of the longest palindrome found so far and return it.