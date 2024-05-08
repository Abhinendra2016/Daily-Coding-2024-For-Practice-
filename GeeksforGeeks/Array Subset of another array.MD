# Problem: Array Subset of Another Array

Given two arrays: `a1[0..n-1]` of size `n` and `a2[0..m-1]` of size `m`, where both arrays may contain duplicate elements. The task is to determine whether array `a2` is a subset of array `a1`. It's important to note that both arrays can be sorted or unsorted. Additionally, each occurrence of a duplicate element within an array is considered as a separate element of the set.

## Example

Input:
a1[] = {11, 7, 1, 13, 21, 3, 7, 3}
a2[] = {11, 3, 7, 1, 7}
Output:
Yes
Explanation:
a2[] is a subset of a1[]

Input:
a1[] = {1, 2, 3, 4, 4, 5, 6}
a2[] = {1, 2, 4}
Output:
Yes
Explanation:
a2[] is a subset of a1[]

Input:
a1[] = {10, 5, 2, 23, 19}
a2[] = {19, 5, 3}
Output:
No
Explanation:
a2[] is not a subset of a1[]

## Solution

```python
def isSubset(a1, a2, n, m):
    freq = {}
    for i in a1:
        freq[i] = freq.get(i, 0) + 1
    for i in a2:
        if i in freq and freq[i] > 0:
            freq[i] -= 1
        else:
            return "No"
    return "Yes"
```
## Approach

To determine if array `a2` is a subset of array `a1`, we can use a dictionary to store the frequency of elements in `a1`.<br> Then, we iterate over `a2` and for each element, we check if it exists in the dictionary and its frequency is greater than 0. <br>If both conditions are met for all elements in `a2`, then `a2` is a subset of `a1`.