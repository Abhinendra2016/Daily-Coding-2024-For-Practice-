# Equilibrium Point


Given an array A of n non-negative numbers, the task is to find the first equilibrium point in the array. An equilibrium point in an array is an index (or position) such that the sum of all elements before that index is the same as the sum of elements after it.

**Note:** Return equilibrium point in 1-based indexing. Return -1 if no such point exists.

### Examples

**Example 1:**

Input:  
n = 5  
A[] = {1, 3, 5, 2, 2}  
Output:  
3  
Explanation:  
Equilibrium point is at position 3 as the sum of elements before it (1+3) is equal to the sum of elements after it (2+2).

**Example 2:**

Input:  
n = 1  
A[] = {1}  
Output:  
1  
Explanation:  
Since there's only one element, it is the only equilibrium point.

## Solution

```python
class Solution:
    # Function to find equilibrium point in the array.
    def equilibriumPoint(self, A, N):
        total = sum(A)
        left_sum = 0
        for i in range(N):
            total -= A[i]
            if left_sum == total:
                return i + 1
            left_sum += A[i]
        return -1
```

<h2>Time Complexity</h2>
The time complexity of this solution is On), where n is the number of elements in the array "A*. This is because the <br>solution involves iterating over the array twice: once to compute the total sum and once to find the equilibrium point.
<h2>Space Complexity</h2>
The space complexity of this solution is O(1). This is because the solution only uses a fixed amount of extra space (variables total' and left_sum*), regardless of the size of the input array.<br>
<h2>Explanation</h2>
The solution uses a two-pass approach to find the equilibrium point:<br>
1. Compute the Total Sum: First, compute the sum of all elements in the array and store it in the variable 'total'.<br>
2. Find the Equilibrium Point: Iterate over the array again, updating the 'total by subtracting the current element and <br>checking if left_sum' (sum of elements before the current index) is equal to the updated 'total' (sum of elements after the current index). If they are equal, return the current index (1-based). Otherwise, update 'left_sum' by adding the current element.<br>
3. Return -1 if No Equilibrium Point Exists: I V, equilibrium point is found after the loop, return -1.<br>
