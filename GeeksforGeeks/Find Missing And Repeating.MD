# Problem: Find Missing And Repeating

Given an unsorted array Arr of size N of positive integers. One number 'A' from set {1, 2,....,N} is missing and one number 'B' occurs twice in array. Find these two numbers.

## Example

Input:
N = 2
Arr[] = {2, 2}
Output: 2 1
Explanation: Repeating number is 2 and 
smallest positive missing number is 1.

Input:
N = 3
Arr[] = {1, 3, 3}
Output: 3 2
Explanation: Repeating number is 3 and 
smallest positive missing number is 2.

## Solution

```python
class Solution:
    def findTwoElement(self, arr, n): 
        arr.sort()
        seen = set()
        mis = 1
        for i in arr:
            if i == mis:
                mis += 1
        for i in range(n):
            if arr[i] not in seen:
                seen.add(arr[i])
            else:
                rep = arr[i]
        return rep, mis
```
## Approach

To find the missing and repeating numbers, we can sort the array first. Then, we can iterate through the array to find the repeating number (which is the number that appears twice) and the missing number (which is the smallest positive integer missing from the array).
