# Problem 1497: Check If Array Pairs Are Divisible by k
Given an array of integers `arr` of even length `n` and an integer `k`, we want to divide the array into exactly `n / 2` pairs such that the sum of each pair is divisible by `k`. The task is to return `true` if this is possible, otherwise `false`.

### Example 1:

Input: arr = [1,2,3,4,5,10,6,7,8,9], k = 5
Output: true
Explanation: Pairs are (1,9),(2,8),(3,7),(4,6), and (5,10).

### Example 2:
Input: arr = [1,2,3,4,5,6], k = 7
Output: true
Explanation: Pairs are (1,6), (2,5), and (3,4).

### Example 3:
Input: arr = [1,2,3,4,5,6], k = 10
Output: false
Explanation: You can try all possible pairs to see that there is no way to divide `arr` into 3 pairs each with sum divisible by 10.

### Example 4:
Input: arr = [1,2,3,4,5,6], k = 10
Output: false
Explanation: You can try all possible pairs to see that there is no way to divide `arr` into 3 pairs each with sum divisible by 10.

### Constraints:
arr.length == n
1 <= n <= 10^5 (n is even)
-10^9 <= arr[i] <= 10^9
1 <= k <= 10^5

<h2> Approach </h2>

The solution leverages the fact that pairs of numbers must have remainders whose sums are divisible by k. Specifically:

For a number x, the remainder when divided by k is x % k.
The remainder of the paired number y must be (k - (x % k)) % k for the sum to be divisible by k.

from collections import Counter
from typing import List

```python
class Solution:
    def canArrange(self, arr: List[int], k: int) -> bool:
        # Count the remainder frequencies
        remainder_count = Counter(x % k for x in arr)
        
        # Check if there are an odd number of elements that are divisible by k
        if remainder_count[0] % 2 != 0:
            return False
        
        # Check for every remainder from 1 to k-1
        for remainder in range(1, k):
            if remainder_count[remainder] != remainder_count[k - remainder]:
                return False
        
        return True
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the number of elements in the array. This is because we iterate through the array once to calculate the remainders, and then we iterate through the possible remainders, which is at most k times.

<h2>Space Complexity</h2>

The space complexity is O(k), where k is the divisor, because we store counts of remainders in a Counter.

