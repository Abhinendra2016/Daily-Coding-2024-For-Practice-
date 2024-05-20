# Problem: Missing Number in Arithmetic Progression

You are given a sorted array of `N` distinct integers that are in the Arithmetic Progression sequence except for one element which is missing from the sequence. You have to find that missing number from the given sequence.

**Note:**
1. A sequence `[arr0, arr1,…, arr(n-1)]` is called an Arithmetic progression if for each 'i' `(0 ≤ i < n - 1)` the value `arr[i+1] − arr[i]` is the same. 
2. There is exactly one missing number in the given sequence.
3. All the numbers present in the sequence are distinct.
4. It is guaranteed that the first and last elements of the sequence are not missing elements.

## Follow Up
The overall run time complexity should be `O(log(N))`.

## Solution
```python
from os import *
from sys import *
from collections import *
from math import *

def missingNumber(arr, n):
    diff = (arr[-1] - arr[0]) // n
    set_arr = set(arr)
    curr = arr[0] + diff
    while curr <= arr[-1]:
        if curr not in set_arr:
            return curr
        curr += diff
    return -1
```