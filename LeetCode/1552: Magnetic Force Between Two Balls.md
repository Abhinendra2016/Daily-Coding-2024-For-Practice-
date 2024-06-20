# Problem 1552: Magnetic Force Between Two Balls

In the universe Earth C-137, Rick discovered a special form of magnetic force between two balls if they are put in his newly invented basket. Rick has `n` empty baskets, the `i`th basket is at `position[i]`. Morty has `m` balls and needs to distribute the balls into the baskets such that the minimum magnetic force between any two balls is maximum.

Rick stated that magnetic force between two different balls at positions `x` and `y` is `|x - y|`.

Given the integer array `position` and the integer `m`. Return the required force.

### Examples

#### Example 1:
Input: position = [1,2,3,4,7], m = 3
Output: 3
Explanation: Distributing the 3 balls into baskets 1, 4, and 7 will make the magnetic force between ball pairs [3, 3, 6]. The minimum magnetic force is 3. We cannot achieve a larger minimum magnetic force than 3.

#### Example 2:

Input: position = [5,4,3,2,1,1000000000], m = 2
Output: 999999999
Explanation: We can use baskets 1 and 1000000000.
### Constraints
- `n == position.length`
- `2 <= n <= 10^5`
- `1 <= position[i] <= 10^9`
- All integers in `position` are distinct.
- `2 <= m <= position.length`

## Solution

```python
from typing import List

class Solution:
    def maxDistance(self, position: List[int], m: int) -> int:
        position.sort()

        def canPlaceBalls(min_force: int) -> bool:
            # Try to place all m balls with at least min_force distance apart
            count = 1
            last_position = position[0]
            for pos in position[1:]:
                if pos - last_position >= min_force:
                    count += 1
                    last_position = pos
                    if count == m:
                        return True
            return False

        # Binary search for the maximum minimum distance
        left, right = 1, position[-1] - position[0]

        while left < right:
            mid = (left + right + 1) // 2
            if canPlaceBalls(mid):
                left = mid
            else:
                right = mid - 1

        return left
```

