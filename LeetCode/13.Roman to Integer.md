# Problem 13: Roman to Integer

Roman numerals are represented by seven different symbols: I, V, X, L, C, D, and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII.Instead, the number four is written as IV. Because the one is before the five, we subtract it, making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:
- I can be placed before V (5) and X (10) to make 4 and 9.
- X can be placed before L (50) and C (100) to make 40 and 90.
- C can be placed before D (500) and M (1000) to make 400 and 900.



## Solution

```python
class Solution:
  def romanToInt(self, s: str) -> int:
    ans = 0
    roman = {'I': 1, 'V': 5, 'X': 10, 'L': 50,
             'C': 100, 'D': 500, 'M': 1000}

    for a, b in zip(s, s[1:]):
      if roman[a] < roman[b]:
        ans -= roman[a]
      else:
        ans += roman[a]

    return ans + roman[s[-1]]
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the length of the input string s. The algorithm iterates through each character in the string once.

<h2>Space Complexity</h2>

The space complexity of this solution is O(1), as it uses only a constant amount of extra space.

<h2>Explanation</h2>

=>I initialize the answer ans to 0.<br>
=>I create a dictionary roman mapping Roman numerals to their integer values.<br>
=>I iterate through each pair of adjacent characters in the input string s using zip(s, s[1:]).<br>
=>For each pair (a, b), if the value of a is less than the value of b, we subtract the value of a from the answer ans. <br>Otherwise, we add the value of a to the answer ans.<br>
Finally, we add the value of the last character in the string s to the answer ans and return ans.