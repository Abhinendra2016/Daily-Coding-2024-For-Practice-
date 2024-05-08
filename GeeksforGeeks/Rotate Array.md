# Problem: Rotate Array

Given an unsorted array `arr[]` of size N. Rotate the array to the left (counter-clockwise direction) by D steps, where D is a positive integer.

## Example

Input:
N = 5, D = 2
arr[] = {1, 2, 3, 4, 5}
Output: 3 4 5 1 2
Explanation: When rotated by 2 elements, the array becomes 3 4 5 1 2.

Input:
N = 10, D = 3
arr[] = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20}
Output: 8 10 12 14 16 18 20 2 4 6
Explanation: When rotated by 3 elements, the array becomes 8 10 12 14 16 18 20 2 4 6.

## Solution

```python
class Solution:
    # Function to rotate an array by d elements in counter-clockwise direction.
    def rotateArr(self, A, D, N):
        # Create a new array to store the rotated elements
        res = [0] * N
        for i in range(N):
            # Calculate the new index after rotation
            res[(i - D) % N] = A[i]
        # Replace the original array with the rotated array
        A.clear()
        A.extend(res)
        return A
```
## Approach

To rotate an array to the left by D steps, we can create a new array of the same size and then copy the elements of the original array to the new array in the rotated positions. After copying all elements, we can replace the original array with the rotated array.