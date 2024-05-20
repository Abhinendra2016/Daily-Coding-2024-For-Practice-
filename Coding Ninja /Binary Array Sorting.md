# Binary Array Sorting
A binary array is an array consisting of only 0s and 1s.

You are given a binary array "arr" of size ‘N’. Your task is to sort the given array and return this array after sorting.

### Example
- **Input**: 
  - arr = [1, 0, 1, 1, 0, 0, 1]
  - N = 7
- **Output**: 
  - [0, 0, 0, 1, 1, 1, 1]

### Explanation
- The input binary array is sorted such that all 0s come before all 1s.

## Solution
```python
def sortBinaryArray(arr, n):
    index = 0
    for i in range(n):
        if arr[i] == 0:
            arr[i], arr[index] = arr[index], arr[i]
            index += 1
    return arr
```