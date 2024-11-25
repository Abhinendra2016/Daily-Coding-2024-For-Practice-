# Problem 773: Sliding Puzzle

## Problem Description

On a 2x3 board, there are five tiles labeled from 1 to 5, and an empty square represented by `0`. A move consists of choosing `0` and a 4-directionally adjacent number and swapping it.

The state of the board is considered solved if and only if the board looks like `[[1, 2, 3], [4, 5, 0]]`.

Given the puzzle board, return the least number of moves required to solve the puzzle. If it is impossible to solve the puzzle, return `-1`.

### Examples

**Example 1:**

Input: board = [[1, 2, 3], [4, 0, 5]] Output: 1 Explanation: Swap the 0 and the 5 in one move.


**Example 2:**

Input: board = [[1, 2, 3], [5, 4, 0]] Output: -1 Explanation: No number of moves will make the board solved.

**Example 3:**

nput: board = [[4, 1, 2], [5, 0, 3]] Output: 5 Explanation: After move 0: [[4,1,2],[5,0,3]] After move 1: [[4,1,2],[0,5,3]] After move 2: [[0,1,2],[4,5,3]] After move 3: [[1,0,2],[4,5,3]] After move 4: [[1,2,0],[4,5,3]] After move 5: [[1,2,3],[4,5,0]]

### Constraints
- `board.length == 2`
- `board[i].length == 3`
- `0 <= board[i][j] <= 5`
- Each value `board[i][j]` is unique.

## Solution

```python
from collections import deque
from typing import List

class Solution:
    def slidingPuzzle(self, board: List[List[int]]) -> int:
        # Define the possible movements on a 2x3 grid
        adj = {
            0: [1, 3],
            1: [0, 2, 4],
            2: [1, 5],
            3: [0, 4],
            4: [1, 3, 5],
            5: [2, 4],
        }

        # Convert the board to a single string format
        b = "".join([str(c) for row in board for c in row])
        # Initialize the queue with (index of '0', board string, number of moves)
        q = deque([(b.index("0"), b, 0)])
        # Set to track visited board states
        visited = set([b])

        while q:
            i, b, length = q.popleft()

            # Check if the current board is the solved state
            if b == "123450":
                return length

            # Try all possible moves from the current state
            for j in adj[i]:
                new_b = list(b)
                # Swap '0' with an adjacent tile
                new_b[i], new_b[j] = new_b[j], new_b[i]
                new_b = "".join(new_b)

                # If the new state hasn't been visited, add it to the queue
                if new_b not in visited:
                    q.append((j, new_b, length + 1))
                    visited.add(new_b)

        # Return -1 if no solution is found
        return -1
```
<h2>Time Complexity</h2>

The time complexity is O(n!) where n is the number of tiles (6 in this case). The state space is relatively small because the board is fixed at 2x3, so a breadth-first search (BFS) works efficiently here.

<h2>Space Complexity</h2>

The space complexity is also O(n!) due to storing visited states in a set for checking previously seen configurations.

<h2>Explanation</h2>

The puzzle is represented as a string for easier manipulation.
A deque is used to perform a BFS, which is suitable for finding the shortest path in terms of moves.
The adjacency list (adj) defines how tiles can be moved from their positions on the 2x3 grid.
If the target configuration "123450" is found, the function returns the number of moves. If all configurations are exhausted without finding the solution, it returns -1.