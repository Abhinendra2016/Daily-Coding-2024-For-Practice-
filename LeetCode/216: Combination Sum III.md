# Problem 216: Combination Sum III

## Problem Description

Find all valid combinations of `k` numbers that sum up to `n` such that the following conditions are true:

- Only numbers `1` through `9` are used.
- Each number is used at most once.

Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

### Example 1:
**Input**: 

k = 3, n = 7

**Output:**
[[1, 2, 4]]
Explanation: 1 + 2 + 4 = 7. There are no other valid combinations.

**Example 2:**
**Input:**
k = 3, n = 9

**Output:**
[[1, 2, 6], [1, 3, 5], [2, 3, 4]]

**Explanation:** 1 + 2 + 6 = 9
1 + 3 + 5 = 9
2 + 3 + 4 = 9

**Example 3:**
**Input:**
k = 4, n = 1

**Output:**
[]

**Explanation:**
There are no valid combinations. Using 4 different numbers in the range [1, 9], the smallest sum is 1 + 2 + 3 + 4 = 10, which is greater than 1.

**Constraints:**
2 <= k <= 9
1 <= n <= 60
Solution

```python
from typing import List

class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        def dfs(start: int, remaining_sum: int):
            if remaining_sum == 0 and len(combination) == k:
                results.append(combination[:])  
                return
            if start > 9 or start > remaining_sum or len(combination) >= k:
                return
            combination.append(start)
            dfs(start + 1, remaining_sum - start)
            combination.pop()
            dfs(start + 1, remaining_sum)
        results = []
        combination = []
        dfs(1, n)
        return results
```




<h2>Time Complexity</h2>

The time complexity of this solution is O(2^9), as for each of the numbers from 1 to 9, we decide whether to include it in the current combination. Since k can be at most 9, we have at most 2^9 subsets to consider.

<h2>Space Complexity</h2>

The space complexity is O(k), which comes from the space used by the combination list to hold the current subset during the depth-first search.

<h2>Explanation</h2>

This problem is solved using backtracking. We explore all possible combinations of numbers from 1 to 9 and check whether they sum up to n. We do this by using a recursive depth-first search (DFS) function that:

Adds a number to the current combination.
Calls itself recursively to continue building the combination.
Removes the number to explore other possibilities (backtracking).