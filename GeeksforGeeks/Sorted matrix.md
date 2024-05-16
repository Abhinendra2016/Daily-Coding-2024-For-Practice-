# Sorted Matrix

## Problem Description

Given an NxN matrix Mat. Sort all elements of the matrix.

### Examples

**Example 1:**

Input:
N=4
Mat=[[10,20,30,40],
[15,25,35,45],
[27,29,37,48],
[32,33,39,50]]
Output:
10 15 20 25
27 29 30 32
33 35 37 39
40 45 48 50
Explanation:
Sorting the matrix gives this result.

**Example 2:**

Input:
N=3
Mat=[[1,5,3],[2,8,7],[4,6,9]]
Output:
1 2 3
4 5 6
7 8 9
Explanation:
Sorting the matrix gives this result.

## Solution

```python
class Solution:
    def sortedMatrix(self, n, mat):
        # Flatten the matrix
        flat_mat = []
        for row in mat:
            flat_mat.extend(row)
        
        # Sort the flattened matrix
        flat_mat.sort()
        
        # Reshape the sorted flattened matrix
        sorted_mat = []
        for i in range(0, len(flat_mat), n):
            sorted_mat.append(flat_mat[i:i+n])
        
        return sorted_mat
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(N^2 * log(N)), where N is the size of the matrix (NxN). This is because we <br>flatten the matrix into a single list of size N^2, then sort this list using Python's built-in sorting algorithm, which has a time complexity of O(N^2 * log(N)).<br>

<h2>Space Complexity</h2>

The space complexity of this solution is O(N^2). This is because we create a flattened copy of the matrix, which requires O(N^2) space, and then create a new matrix of the same size to store the sorted elements.