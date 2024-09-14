# Problem 2419: Longest Subarray With Maximum Bitwise AND

You are given an integer array `nums` of size `n`. Consider a non-empty subarray from `nums` that has the maximum possible bitwise AND.

In other words, let `k` be the maximum value of the bitwise AND of any subarray of `nums`. Then, only subarrays with a bitwise AND equal to `k` should be considered.

Return the length of the longest such subarray.

The **bitwise AND** of an array is the bitwise AND of all the numbers in it.

A subarray is a contiguous sequence of elements within an array.

### Example 1:

**Input**: 
nums = [1, 2, 3, 3, 2, 2]
**Output**: 
2

**Explanation**: 
The maximum possible bitwise AND of a subarray is `3`.  
The longest subarray with that value is `[3, 3]`, so we return `2`.

### Example 2:
nums = [1, 2, 3, 4]
**Input**: 
1
**Output**: 
1

**Explanation**: 
The maximum possible bitwise AND of a subarray is `4`.  
The longest subarray with that value is `[4]`, so we return `1`.

### Constraints:

- `1 <= nums.length <= 10^5`
- `1 <= nums[i] <= 10^6`

---

## Solution

```python
class Solution:
    def longestSubarray(self, nums: list[int]) -> int:
        ans = 0
        maxIndex = 0
        sameNumLength = 0
        for i, num in enumerate(nums):
            if nums[i] == nums[maxIndex]:
                sameNumLength += 1
                ans = max(ans, sameNumLength)
            elif nums[i] > nums[maxIndex]:
                maxIndex = i
                sameNumLength = 1
                ans = 1
            else:
                sameNumLength = 0
        return ans
```
<h2>Time Complexity</h2>
The time complexity of this solution is O(n) where n is the length of the input array nums. This is because we iterate through the array exactly once to determine the length of the longest subarray with the maximum bitwise AND.

<h2>Space Complexity</h2>
The space complexity of the solution is O(1) since we only use a few variables (ans, maxIndex, and sameNumLength) to keep track of the current state, and no additional data structures are used that grow with the input size.

