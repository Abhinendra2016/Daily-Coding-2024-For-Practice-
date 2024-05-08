# Problem: Find Minimum and Maximum Element in an Array

Given an array `A` of size `N` of integers, your task is to find the minimum and maximum elements in the array.

## Example

Input:
N = 6
A[] = {3, 2, 1, 56, 10000, 167}
Output: 1 10000
Explanation: The minimum and maximum elements of the array are 1 and 10000, respectively.

Input:
N = 5
A[] = {1, 345, 234, 21, 56789}
Output: 1 56789
Explanation: The minimum and maximum elements of the array are 1 and 56789, respectively.

## Solution

```python
def getMinMax(a, n):
    if n == 0:
        return None, None

    min_element = max_element = a[0]
    for i in range(1, n):
        if a[i] < min_element:
            min_element = a[i]
        if a[i] > max_element:
            max_element = a[i]

    return min_element, max_element
```
## Approach

To find the minimum and maximum elements in an array, we can iterate over the array and keep track of the minimum and maximum elements seen so far.<br>

- Initialize `min_element` and `max_element` to the first element of the array.<br>
- Iterate over the array starting from the second element.<br>
- For each element, if it is less than `min_element`, update `min_element`. If it is greater than `max_element`, update `max_element`.<br>
- Return `min_element` and `max_element` as the result.<br>