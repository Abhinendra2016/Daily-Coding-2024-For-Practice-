# Problem: Product Array Puzzle

You are given an array of 'N' integers. You need to return another array 'product' such that 'product[i]' contains the product of all the arrays except the element at the ith position in the given array.

## Note
As the product of elements can be very large you need to return the answer in mod (10^9+7).

## Follow Up
Try to do this without using the division operator '/', in constant space. The output array does not count as extra space for the purpose of space complexity analysis.

## Solution

```python
def productPuzzle(arr):
    n = len(arr)
    leftProducts = [1] * n
    rightProducts = [1] * n

    leftProduct = 1
    for i in range(1, n):
        leftProduct = (leftProduct * arr[i - 1]) % (10 ** 9 + 7)
        leftProducts[i] = leftProduct

    rightProduct = 1
    for i in range(n - 2, -1, -1):
        rightProduct = (rightProduct * arr[i + 1]) % (10 ** 9 + 7)
        rightProducts[i] = rightProduct

    result = [(leftProducts[i] * rightProducts[i]) % (10 ** 9 + 7) for i in range(n)]
    return result
```
<h2>Explanation</h2>

We create two arrays, leftProducts and rightProducts, to store the product of elements to the left and right of each element respectively.<br>
We initialize the product of elements to the left of the first element as 1 and calculate the product of elements to the left of each element in the leftProducts array.<br>
Similarly, we initialize the product of elements to the right of the last element as 1 and calculate the product of elements to the right of each element in the rightProducts array.<br>
Finally, we calculate the product of elements at each position by multiplying the corresponding elements from the leftProducts and rightProducts arrays, taking care to use modulo (10^9+7) to avoid overflow.<br>

