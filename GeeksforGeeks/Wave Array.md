# Problem: Wave Array

Given a sorted array `arr[]` of distinct integers. Sort the array into a wave-like array (In Place). In other words, arrange the elements into a sequence such that `arr[1] >= arr[2] <= arr[3] >= arr[4] <= arr[5]...`.

If there are multiple solutions, find the lexicographically smallest one.

Note: The given array is sorted in ascending order, and you don't need to return anything to make changes in the original array itself.

## Example

Input:
n = 5
arr[] = {1, 2, 3, 4, 5}
Output: 2 1 4 3 5
Explanation: Array elements after sorting it in wave form are 2 1 4 3 5.

Input:
n = 6
arr[] = {2, 4, 7, 8, 9, 10}
Output: 4 2 8 7 10 9
Explanation: Array elements after sorting it in wave form are 4 2 8 7 10 9.

## Solution

```python
from typing import List

class Solution:
    def convertToWave(self, n: int, a: List[int]) -> None:
        for i in range(0, n - 1, 2):
            a[i], a[i + 1] = a[i + 1], a[i]
```

## Approach

To convert the given array to a wave array, we can simply iterate over the array and swap adjacent elements pairwise. This way, the array will be transformed into a wave-like array where each element is either greater than or less than its adjacent elements, depending on its position.