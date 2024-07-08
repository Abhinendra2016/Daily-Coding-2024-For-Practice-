# Find Missing and Repeating Numbers

## Problem Statement

You are given an array of size `N`. The elements of the array are in the range from `1` to `N`. Ideally, the array should contain elements from `1` to `N`. However, due to some miscalculations, there is a number `R` in the range `[1, N]` which appears in the array twice, and another number `M` in the range `[1, N]` which is missing from the array.

Your task is to find the missing number (`M`) and the repeating number (`R`).

### Example

Consider an array of size six. The elements of the array are `{6, 4, 3, 5, 5, 1}`. 

The array should contain elements from one to six. Here, `2` is not present and `5` is occurring twice. Thus, `2` is the missing number (`M`) and `5` is the repeating number (`R`).

## Follow-Up

Can you solve this problem in linear time and constant additional space?

## Solution

Here is a Python function to solve the problem:

```python
from math import *
from collections import *
from sys import *
from os import *

def findRepeating(arr, n):
    lis = []
    for ele in arr:
        if ele in lis:
            return ele
        lis.append(ele)
    return [-1]

def findMissing(arr, n):
    arr = set(arr)
    nums = set(range(1, n+1))
    if arr == nums:
        return 0
    lis = list(nums - arr)
    return lis[0]

def missingAndRepeating(arr, n):
    arr.sort()
    return [findMissing(arr, n), findRepeating(arr, n)]
```



