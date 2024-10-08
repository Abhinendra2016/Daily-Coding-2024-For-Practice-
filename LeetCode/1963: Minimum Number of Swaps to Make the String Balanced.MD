# Problem 1963: Minimum Number of Swaps to Make the String Balanced

## Problem Description

You are given a 0-indexed string `s` of even length `n`. The string consists of exactly `n / 2` opening brackets `[` and `n / 2` closing brackets `]`.

A string is called balanced if and only if:
1. It is the empty string, or
2. It can be written as AB, where both A and B are balanced strings, or
3. It can be written as `[C]`, where C is a balanced string.

You may swap the brackets at any two indices any number of times.

Return the minimum number of swaps to make `s` balanced.

### Example 1:

**Input**: 

s = "][]["
Output:
1

Explanation: You can make the string balanced by swapping index 0 with index 3.
The resulting string is [[]].

Example 2:
Input:

s = "]]][[["

Output:
2

Explanation: You can do the following to make the string balanced:

Swap index 0 with index 4: s = "[]][][".
Swap index 1 with index 5: s = "[[][]]".
The resulting string is [[][]].

Example 3:
Input:

s = "[]"

Output:
0

Explanation: The string is already balanced.

Constraints

n == s.length
2 <= n <= 10^6
n is even.
s[i] is either '[' or ']'.
The number of opening brackets [ equals n / 2, and the number of closing brackets ] equals n / 2.

```python
class Solution:
    def minSwaps(self, s: str) -> int:
        unmatched = 0
        for c in s:
            if c == '[':
                unmatched += 1
            elif unmatched > 0:
                unmatched -= 1
        return (unmatched + 1) // 2
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the length of the string. This is because the algorithm iterates through the string once to count the unmatched brackets.

<h2>Space Complexity</h2>

The space complexity is O(1) since the algorithm only uses a constant amount of extra space, regardless of the input size.

<h2>Explanation</h2>

The goal is to determine the minimum number of swaps needed to balance the string. We track the number of unmatched opening brackets as we traverse the string. For every unmatched closing bracket, we attempt to balance it with an unmatched opening bracket. The result is the minimum number of swaps needed to achieve balance.