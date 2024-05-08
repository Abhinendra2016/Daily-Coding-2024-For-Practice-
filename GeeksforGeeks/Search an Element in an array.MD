# Problem: Search an Element in an Array

Given an integer array `arr` and another integer `element`, the task is to find if the given element is present in the array or not.

## Example

Input:
n = 4
arr[] = {1, 2, 3, 4}
x = 3
Output: 2
Explanation: There is one test case with an array {1, 2, 3, 4} and an element to be searched as 3. Since 3 is present at index 2, the output is 2.

Input:
n = 5
arr[] = {1, 2, 3, 4, 5}
x = 5
Output: 4
Explanation: For array elements {1, 2, 3, 4, 5}, the element to be searched is 5 and it is at index 4. So, the output is 4.


## Solution

```python
class Solution:
    # Complete the below function
    def search(self, arr, N, X):
        # Iterate over the array
        for i in range(N):
            # Check if the current element is equal to X
            if arr[i] == X:
                return i
        # If the element is not found, return -1
        return -1
```
## Approach

To search for an element in an array, we can simply iterate over the array and check if each element is equal to the given element `X`. If we find the element, we return its index. If we reach the end of the array without finding the element, we return -1 to indicate that the element is not present in the array.
