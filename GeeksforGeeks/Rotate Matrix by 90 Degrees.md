# Problem: Rotate Matrix by 90 Degrees

Given a square matrix of size N x N, rotate it by 90 degrees in the anti-clockwise direction without using any extra space.

## Example

Input:
N = 3
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
Output:
Rotated Matrix:
[
  [3, 6, 9],
  [2, 5, 8],
  [1, 4, 7]
]

Input:
N = 2
matrix = [
  [1, 2],
  [3, 4]
]
Output:
Rotated Matrix:
[
  [2, 4],
  [1, 3]
]

## Solution

```python
class Solution:
    
    # Function to rotate matrix anticlockwise by 90 degrees.
    def rotateby90(self, matrix, n): 
        for rows in matrix:
            rows.reverse()   # reverse the matrix first
        
        for i in range(n):
            for j in range(i, n):     
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]  # swap the row and col element
        
        return matrix
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(N^2), where N is the size of the input matrix. This is because we iterate through all elements of the matrix twice.

<h2>Space Complexity</h2>

The space complexity of this solution is O(1), as we do not use any extra space.

<h2>Explanation</h2>

We first reverse each row of the matrix to get the matrix rotated by 180 degrees.
Then, we swap the elements symmetrically across the main diagonal to get the matrix rotated by 270 degrees (90 degrees anti-clockwise).
