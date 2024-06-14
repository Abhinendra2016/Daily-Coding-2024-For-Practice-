# Problem 945: Minimum Increment to Make Array Unique

You are given an integer array `nums`. In one move, you can pick an index `i` where `0 <= i < nums.length` and increment `nums[i]` by 1.

Return the minimum number of moves to make every value in `nums` unique.

The test cases are generated so that the answer fits in a 32-bit integer.

## Examples

### Example 1

Input: nums = [1,2,2]
Output: 1
Explanation: After 1 move, the array could be [1, 2, 3].

### Example 2

Input: nums = [3,2,1,2,1,7]
Output: 6
Explanation: After 6 moves, the array could be [3, 4, 1, 2, 5, 7].
It can be shown with 5 or less moves that it is impossible for the array to have all unique values.

## Constraints

1 <= nums.length <= 10^5
0 <= nums[i] <= 10^5

```python
from typing import List
class Solution:
    def minIncrementForUnique(self, nums: List[int]) -> int:
        # Sort the input list to handle elements in ascending order
        nums.sort()

        # Initialize the variables to keep track of the total increments
        # and the minimum available value for the next unique element
        ans = 0
        minAvailable = 0

        # Iterate through the sorted list of numbers
        for num in nums:
            # Calculate the increment needed for the current number to be unique
            ans += max(minAvailable - num, 0)

            # Update the minimum available value for the next unique element
            minAvailable = max(minAvailable, num) + 1

        return ans
```

<h2>Time Complexity</h2>

The time complexity of this solution is O(n log n). This is because the most time-consuming operation is the sorting of the<br> nums array, which takes O(n log n) time. The subsequent iteration through the sorted array takes O(n) time, but this is dominated by the sorting step.<br>

<h2>Space Complexity</h2>

The space complexity of this solution is O(1) if we ignore the space required for the input list nums. The sorting <br>operation may require additional space depending on the sorting algorithm used, but this is typically considered as O(n log n) in auxiliary space complexity. Overall, the space complexity remains O(1) as we are not using any additional data <br>structures that grow with the input size.<br>
