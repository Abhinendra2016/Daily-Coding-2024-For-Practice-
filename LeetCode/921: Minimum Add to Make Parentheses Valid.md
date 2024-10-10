# Problem 921: Minimum Add to Make Parentheses Valid

A parentheses string is valid if and only if:

- It is the empty string,
- It can be written as AB (A concatenated with B), where A and B are valid strings, or
- It can be written as `(A)`, where A is a valid string.

You are given a parentheses string `s`. In one move, you can insert a parenthesis at any position of the string.

For example, if `s = "()))"`, you can insert an opening parenthesis to be `"(()))"` or a closing parenthesis to be `"()))))"`.

Return the minimum number of moves required to make `s` valid.

## Example 1:

Input: s = "())"
Output: 1
## Example 2:
Example 2:
Input: s = "((("
Output: 3


```python
class Solution:
  def minAddToMakeValid(self, s: str) -> int:
    l = 0  # Count of unmatched '('
    r = 0  # Count of unmatched ')'
    for c in s:
      if c == '(':
        l += 1
      else:  # c == ')'
        if l == 0:
          r += 1
        else:
          l -= 1
    return l + r
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the length of the input string s. This is because we only make one pass through the string.

<h2>Space Complexity</h2>

The space complexity is O(1), as we are only using a fixed amount of extra space to store the counts of unmatched parentheses.

<h2>Explanation</h2>

The solution counts the number of unmatched opening and closing parentheses.

For each '(', we increase the count of unmatched opening parentheses l.
For each ')', we check if there is an unmatched '(' to match it with. If there is, we reduce the count of unmatched opening parentheses (l). Otherwise, we increase the count of unmatched closing parentheses (r).
The result is the sum of unmatched opening and closing parentheses, which gives the minimum number of insertions required to make the string valid.
