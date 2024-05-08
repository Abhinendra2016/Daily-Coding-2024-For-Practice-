# Problem: Missing number in array

Given an array of size N-1 such that it only contains distinct integers in the range of 1 to N. Find the missing element.

## Example

Input:
N = 5
A[] = {1, 2, 3, 5}
Output: 4

Input:
N = 10
A[] = {6, 1, 2, 8, 3, 4, 7, 10, 5}
Output: 9


## Solution

```python
class Solution:
    def missingNumber(self, array, n):
        total_sum = (n * (n + 1)) // 2
        array_sum = sum(array)
        return total_sum - array_sum
```
## Approach

To find the missing number in the array, we can use the formula for the sum of the first N natural numbers: sum = N * (N + 1) / 2. We first calculate the total sum of the first N numbers. Then, we sum all the elements in the array to get the sum of the N-1 numbers present. The missing number will be the difference between the total sum and the sum of the array elements.