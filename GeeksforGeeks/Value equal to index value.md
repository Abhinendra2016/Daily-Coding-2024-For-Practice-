# Problem: Value Equal to Index Value

Given an array `Arr` of `N` positive integers. Your task is to find the elements whose value is equal to that of its index value (considering 1-based indexing).

Note: There can be more than one element in the array which have the same value as its index. You need to include every such element's index.

## Example

Input:
N = 5
Arr[] = {15, 2, 45, 12, 7}
Output: 2
Explanation: Only `Arr[2] = 2` exists here.

Input:
N = 1
Arr[] = {1}
Output: 1
Explanation: Here `Arr[1] = 1` exists.

## Your Task

You don't need to read input or print anything. Your task is to complete the function `valueEqualToIndex()` which takes the array of integers `arr[]` and `n` as parameters and returns an array of indices where the given conditions are satisfied. When there is no such element exists then return an empty array of length 0. For C users, you need to modify the array `arr`, in place such that the indices not in the final answer should be marked 0.

## Solution

```python
class Solution:
    def valueEqualToIndex(self, arr, n):
        result = []
        for i, val in enumerate(arr):
            if (i + 1) == val:
                result.append(val)

        return result
```
<h2>Explanation</h2>

We iterate through the array arr using enumerate() to get both the index i and the value val at that index.<br>
We check if i + 1 is equal to val (considering 1-based indexing) and if so, we append val to the result list.<br>
Finally, we return the result list containing indices where the value is equal to the index.<br>