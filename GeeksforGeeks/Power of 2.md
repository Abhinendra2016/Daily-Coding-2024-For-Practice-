# Problem: Power of 2

Given a non-negative integer `N`, the task is to check if `N` is a power of 2. More formally, check if `N` can be expressed as 2^x for some integer `x`. Return true if `N` is a power of 2 else return false.

## Example

Input: 
N = 8
Output: 
YES
Explanation:
8 is equal to 2 raised to 3 (2^3 = 8).

Input: 
N = 98
Output: 
NO
Explanation: 
98 cannot be obtained by any power of 2.

## Solution

```python
class Solution:
    ##Complete this function
    # Function to check if given number n is a power of two.
    def isPowerofTwo(self, n: int) -> bool:
        return n != 0 and (n & (n - 1)) == 0
```
## Approach

To check if a number is a power of 2, we can use the property that for any number `N`, if `N` is a power of 2, then it has only one bit set in its binary representation. So, if we perform a bitwise AND operation between `N` and `N - 1`, and the result is 0, then `N` is a power of 2.