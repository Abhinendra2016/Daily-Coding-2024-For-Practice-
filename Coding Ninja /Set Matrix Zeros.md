# Problem: Set Matrix Zeros

Given an ‘N’ x ‘M’ integer matrix, if an element is 0, set its entire row and column to 0's, and return the matrix. In particular, your task is to modify it in such a way that if a cell has a value 0 (`matrix[i][j] == 0`), then all the cells of the `ith` row and `jth` column should be changed to 0.


## Solution

```python
from typing import List

def setZeros(matrix: List[List[int]]) -> None:
    if not matrix or not matrix[0]:
        return
    rows, cols = len(matrix), len(matrix[0])
    zero_rows, zero_cols = set(), set()
    # Identify the rows and columns that contain zeros
    for i in range(rows):
        for j in range(cols):
            if matrix[i][j] == 0:
                zero_rows.add(i)
                zero_cols.add(j)
    # Set entire rows and columns to zero
    for row in zero_rows:
        for j in range(cols):
            matrix[row][j] = 0
    for col in zero_cols:
        for i in range(rows):
            matrix[i][col] = 0
```
<h2>Explanation</h2>

We initialize two sets, zero_rows and zero_cols, to store the indices of rows and columns that contain zeros.<h2>
We iterate through the matrix to identify the rows and columns that contain zeros, and add their indices to the respective sets.<h2>
Finally, we iterate through the sets and set the entire rows and columns to zero in the matrix.<h2>

