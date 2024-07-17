# First Missing Positive

You are given an array 'ARR' of integers of length N. Your task is to find the first missing positive integer in linear time and constant space. In other words, find the lowest positive integer that does not exist in the array. The array can have negative numbers as well.

For example, the input `[3, 4, -1, 1]` should give output 2 because it is the smallest positive number that is missing in the input array.

## Sample Input 1 :
1
5
3 2 -6 1 0

## Sample Output 1:
4


## Explanation for Input 1:
The first positive number is 1 and it is present in the array similarly 2 and 3 are also present in the array. 4 is missing from the array. Thus, the minimum positive integer that is missing is 4.

## Sample Input 2 :
1
5
0 1 2 3 4

## Sample Output 2:
5

## Solution

```python
from os import *
from sys import *
from collections import *
from math import *

def firstMissing(arr, n):
    found = False
    ans = set(arr)
    for i in range(1,n+1):
        if i not in ans:
            return i
    if found==False:
        return n+1

# Main Code
t=int(input())

for j in range(t):
    n=int(input())
    arr=[int(i) for i in input().split()]
    ans = firstMissing(arr,n)

    print(ans)
```
<h2>Time Complexity</h2>
The time complexity of this solution is O(n) where n is the length of the array. This is because we are using a set to store the elements of the array and then checking for the first missing positive integer in a single pass through the array.<br>
<h2>Space Complexity</h2>
The space complexity of this solution is O(n) because we are using a set to store the elements of the array.<br>
<h2>Explanation</h2>
1. First, we convert the array into a set to allow for O(1) time complexity checks for existence of elements.<br>
2. We then iterate through numbers from 1 to n (the length of the array).<br>
3. For each number, we check if it is in the set. If it is not, that number is our first missing positive integer.<br>
4. If we complete the loop and find that all numbers from 1 to n are in the set, then the first missing positive integer is n+1.<br>
