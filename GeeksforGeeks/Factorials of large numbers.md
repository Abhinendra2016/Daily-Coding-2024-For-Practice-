# Problem: Factorials of Large Numbers

Given an integer N, find its factorial. Return a list of integers denoting the digits that make up the factorial of N.

## Example

Input: N = 5
Output: 120
Explanation: 5! = 1 * 2 * 3 * 4 * 5 = 120

Input: N = 10
Output: 3628800
Explanation: 10! = 1 * 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9 * 10 = 3628800

Expected Time Complexity : O(N^2)
Expected Auxilliary Space : O(1)


## Solution

```python
class Solution:
    def factorial(self, N):
        f = 1
        for i in range(1, N + 1):
            f *= i
        return [int(digit) for digit in str(f)]
```
## Approach

To find the factorial of a number, we can simply iterate from 1 to N and multiply the result by each number. We can store the result in a variable and return it as a list of digits.