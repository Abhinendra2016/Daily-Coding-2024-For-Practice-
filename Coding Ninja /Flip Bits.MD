# Flip Bits

## Problem Statement

You are given an array of integers `ARR[]` of size `N` consisting of zeros and ones. You have to select a subset and flip the bits of that subset. You have to return the count of maximum ones that you can obtain by flipping the chosen sub-array at most once.

A flip operation is one in which you turn 1 into 0 and 0 into 1.

### Example:

If you are given an array `{1, 1, 0, 0, 1}`, then you will have to return the count of maximum ones you can obtain by flipping any one chosen sub-array at most once. Here, you will clearly choose the sub-array from index 2 to 3 and then flip its bits. So, the final array comes out to be `{1, 1, 1, 1, 1}` which contains five ones, and you will return `5`.

### Constraints:

- \(1 \leq T \leq 100\)
- \(1 \leq N \leq 10^4\)
- \(0 \leq ARR[i] \leq 1\)

**Time Limit**: 1 second

### Sample Input 1:
3
5
1 0 0 1 0
4
1 1 1 0
5
0 0 1 0 0
### Sample Output 1:
4
4
4

**Explanation for Sample Input 1:**

For the first test case:
We can perform a flip operation in the range `[1, 2]`. After the flip operation, the array is: `1 1 1 1 0`, and so the answer will be `4`.

Similarly, in the second test case:
We can perform a flip operation in the range `[3, 3]`. After the flip operation, the array is: `1 1 1 1`, and so the answer will be `4`.

Finally, for the third test case:
We can perform a flip operation in the range `[0, 4]`. After the flip operation, the array is: `1 1 0 1 1`, and so the answer will be `4`.

### Sample Input 2:
3
5
0 0 0 0 0
5
1 1 1 1 1
8
1 0 1 0 1 0 1 0
### Sample Output 2:
5
5
5

## Solution

The solution involves traversing the array and using a modified version of Kadane’s Algorithm to find the sub-array which, when flipped, maximizes the count of ones.

### Code

```python
def flipBits(arr, n):
    zeros = 0
    ones = 0
    mx = 0
    for i in arr:
        if i == 0:
            zeros += 1
        else:
            zeros -= 1
            ones += 1
        if zeros > mx:
            mx = zeros
        if zeros < 0:
            zeros = 0
    return mx + ones
```

## Solution

The solution involves traversing the array and using a modified version of Kadane’s Algorithm to find the sub-array which, when flipped, maximizes the count of ones.

### Code

```python
def flipBits(arr, n):
    zeros = 0
    ones = 0
    mx = 0
    for i in arr:
        if i == 0:
            zeros += 1
        else:
            zeros -= 1
            ones += 1
        if zeros > mx:
            mx = zeros
        if zeros < 0:
            zeros = 0
    return mx + ones
```
