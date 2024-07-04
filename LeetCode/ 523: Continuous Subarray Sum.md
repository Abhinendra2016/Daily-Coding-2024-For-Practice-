# Problem 523: Continuous Subarray Sum

Given an integer array `nums` and an integer `k`, return `true` if `nums` has a good subarray or `false` otherwise.

A good subarray is a subarray where:

- Its length is at least two, and
- The sum of the elements of the subarray is a multiple of `k`.

Note that:

- A subarray is a contiguous part of the array.
- An integer `x` is a multiple of `k` if there exists an integer `n` such that `x = n * k`. `0` is always a multiple of `k`.

## Examples

### Example 1:

Input: nums = [23,2,4,6,7], k = 6
Output: true
Explanation: [2, 4] is a continuous subarray of size 2 whose elements sum up to 6.

### Example 2:

Input: nums = [23,2,6,4,7], k = 6
Output: true
Explanation: [23, 2, 6, 4, 7] is a continuous subarray of size 5 whose elements sum up to 42. 42 is a multiple of 6 because 42 = 7 \* 6 and 7 is an integer

### Example 3:

Input: nums = [23,2,6,4,7], k = 13
Output: false

## Constraints

- `1 <= nums.length <= 10^5`
- `0 <= nums[i] <= 10^9`
- `0 <= sum(nums[i]) <= 2^31 - 1`
- `1 <= k <= 2^31 - 1`

## Solution

```python
from typing import List

class Solution:
    def checkSubarraySum(self, nums: List[int], k: int) -> bool:
        prefix = 0
        prefixToIndex = {0: -1}

        for i, num in enumerate(nums):
            prefix += num
            if k != 0:
                prefix %= k
            if prefix in prefixToIndex:
                if i - prefixToIndex[prefix] > 1:
                    return True
            else:
                prefixToIndex[prefix] = i

        return False
```

<h2>Time Complexity</h2>
The time complexity of this solution is O(n + m), where n is the length of nums1 and m is the length of nums2. This is because we iterate through both arrays once.<br>

<h2>Space Complexity</h2>

The space complexity is O(min(n, m)) because we store the counts of the smaller array's elements.<br>
