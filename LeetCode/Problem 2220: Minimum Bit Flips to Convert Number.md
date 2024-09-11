# Problem 2220: Minimum Bit Flips to Convert Number

A bit flip of a number `x` is choosing a bit in the binary representation of `x` and flipping it from either `0` to `1` or `1` to `0`.<br>

For example, for `x = 7`, the binary representation is `111`, and we may choose any bit (including any leading zeros not shown) and flip it. We can flip the first bit from the right to get `110`, flip the second bit from the right to get `101`, flip the fifth bit from the right (a leading zero) to get `10111`, etc.<br>

Given two integers `start` and `goal`, return the minimum number of bit flips to convert `start` to `goal`.<br>

## Example 1:

### Input:
start = 3, goal = 4<br>

### Output:
3

### Explanation:
The binary representation of `3` and `4` are `011` and `100` respectively. We can convert `3` to `4` in 3 steps:<br>
- Flip the first bit from the right: `011 -> 010`.<br>
- Flip the second bit from the right: `010 -> 000`.<br>
- Flip the third bit from the right: `000 -> 100`.<br>

It can be shown we cannot convert `3` to `4` in less than 3 steps. Hence, we return `3`.<br>

## Constraints:
- `0 <= start, goal <= 10^9`

## Solution
```python
class Solution:
  def minBitFlips(self, start: int, goal: int) -> int:
    return (start ^ goal).bit_count()
```
<h2>Time Complexity</h2>

The time complexity is O(n) where n is the number of bits in the binary representation of the largest number between start and goal. In this case, for start, goal <= 10^9, it is constant since the maximum number of bits required is 30.<br>

<h2>Space Complexity</h2>

The space complexity is O(1) since no extra space other than a few variables is required.

<h2>Explanation</h2>
XOR Operation: The key to solving the problem is realizing that performing an XOR between start and goal will give a binary number where each 1 represents a bit that needs to be flipped.<br>
Counting Flips: Using the bit_count() method (or bin(x).count('1') in older Python versions) will count the number of 1s in the XOR result, which tells us how many bits differ between the two numbers.<br>