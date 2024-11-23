# Problem 1861: Rotating the Box

You are given an `m x n` matrix of characters `box` representing a side-view of a box. Each cell of the box is one of the following:<br>

- A stone `'#'`
- A stationary obstacle `'*'`
- Empty `'.'`

The box is rotated 90 degrees clockwise, causing some of the stones to fall due to gravity. Each stone falls down until it lands on an obstacle, another stone, or the bottom of the box. Gravity does not affect the obstacles' positions, and the inertia from the box's rotation does not affect the stones' horizontal positions.
<br>
It is guaranteed that each stone in `box` rests on an obstacle, another stone, or the bottom of the box.<br>
<br>
Return an `n x m` matrix representing the box after the rotation described above.<br>

## Examples

### Example 1
**Input:**
box = [["#",".","#"]]
**Output:**
[["."], ["#"], ["#"]]

### Example 2
**Input:**
box = [["#",".","","."], ["#","#","","."]]
**Output:**
[["#","."], ["#","#"], ["",""], [".","."]]

### Example 3
**Input:**
box = [["#","#","",".","","."], ["#","#","#","*",".","."], ["#","#","#",".","#","."]]
**Output:**
[[".","#","#"], ["#","#",""], ["#","","."], ["#",".","*"], ["#",".","."], [".",".","."]]


## Constraints
- `m == box.length`
- `n == box[i].length`
- `1 <= m, n <= 500`
- `box[i][j]` is either `'#'`, `'*'`, or `'.'`.

## Solution

```python
class Solution:
    def rotateTheBox(self, box: list[list[str]]) -> list[list[str]]:
        m = len(box)
        n = len(box[0])
        rotated = [['.'] * m for _ in range(n)]
        for i in range(m):
            k = n - 1
            for j in reversed(range(n)):
                if box[i][j] != '.':
                    if box[i][j] == '*':
                        k = j
                    rotated[k][m - i - 1] = box[i][j]
                    k -= 1
        return [''.join(row) for row in rotated]
```
<H2>Time Complexity</H2>

The solution has a time complexity of <br>
O(m×n)<br>
O(m×n), where:<br>
m is the number of rows in the box.<br>
n is the number of columns.<br>
This is due to iterating over each cell in the box to simulate gravity and perform the rotation.<br>
<H2>Space Complexity</H2>

The space complexity is<br>
O(m×n)
O(m×n) because:<br>
We create a new n x m matrix to store the rotated result.
