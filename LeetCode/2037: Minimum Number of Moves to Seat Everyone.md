# Problem 2037: Minimum Number of Moves to Seat Everyone

There are n seats and n students in a room. You are given an array `seats` of length n, where `seats[i]` is the position of the ith seat. You are also given the array `students` of length n, where `students[j]` is the position of the jth student.

You may perform the following move any number of times:

- Increase or decrease the position of the ith student by 1 (i.e., moving the ith student from position x to x + 1 or x - 1).

Return the minimum number of moves required to move each student to a seat such that no two students are in the same seat.

**Note**: There may be multiple seats or students in the same position at the beginning.

## Examples

### Example 1

Input: seats = [3,1,5], students = [2,7,4]
Output: 4
Explanation: The students are moved as follows:

- The first student is moved from position 2 to position 1 using 1 move.
- The second student is moved from position 7 to position 5 using 2 moves.
- The third student is moved from position 4 to position 3 using 1 move.
  In total, 1 + 2 + 1 = 4 moves were used.

### Example 2

Input: seats = [4,1,5,9], students = [1,3,2,6]
Output: 7
Explanation: The students are moved as follows:

- The first student is not moved.
- The second student is moved from position 3 to position 4 using 1 move.
- The third student is moved from position 2 to position 5 using 3 moves.
- The fourth student is moved from position 6 to position 9 using 3 moves.
  In total, 0 + 1 + 3 + 3 = 7 moves were used.

### Example 3

Input: seats = [2,2,6,6], students = [1,3,2,6]
Output: 4
Explanation: Note that there are two seats at position 2 and two seats at position 6.
The students are moved as follows:

- The first student is moved from position 1 to position 2 using 1 move.
- The second student is moved from position 3 to position 6 using 3 moves.
- The third student is not moved.
- The fourth student is not moved.
  In total, 1 + 3 + 0 + 0 = 4 moves were used.

### Constraints

n == seats.length == students.length
1 <= n <= 100
1 <= seats[i], students[j] <= 100

### Solution

```python
from typing import List

class Solution:
    def minMovesToSeat(self, seats: List[int], students: List[int]) -> int:
        # Step 1: Sort the seats list
        sorted_seats = sorted(seats)
        # Step 2: Sort the students list
        sorted_students = sorted(students)
        # Step 3: Initialize the total moves to 0
        total_moves = 0
        # Step 4: Iterate over the sorted seats and students simultaneously
        for seat, student in zip(sorted_seats, sorted_students):
            # Step 5: Calculate the absolute difference between the current seat and student
            move = abs(seat - student)
            # Step 6: Add the move to the total moves
            total_moves += move
        # Step 7: Return the total number of moves required
        return total_moves
```
<h2>Time Complexity</h2>
The time complexity of this solution is O(n log n). This is because the most time-consuming operations are the sorting of <br>the seats and students arrays, each of which takes O(n log n) time. The subsequent iteration over the arrays takes O(n) time, which is dominated by the sorting step.<br>

<h2>Space Complexity</h2>
The space complexity of this solution is O(1), assuming that the input arrays seats and students can be sorted in place. If we consider the space required for the sorted arrays separately, it would be O(n). However, since we do not use any additional data structures that grow with the input size, the overall space complexity remains O(1).<br>
