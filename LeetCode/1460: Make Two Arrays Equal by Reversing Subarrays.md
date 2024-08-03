# Problem 1460: Make Two Arrays Equal by Reversing Subarrays

You are given two integer arrays of equal length `target` and `arr`. In one step, you can select any non-empty subarray of `arr` and reverse it. You are allowed to make any number of steps.

Return `true` if you can make `arr` equal to `target` or `false` otherwise.

## Examples

### Example 1

**Input:**

target = [1, 2, 3, 4]
arr = [2, 4, 1, 3]

**Output:**
true

**Explanation:**

You can follow the next steps to convert arr to target:

Reverse subarray [2, 4, 1], arr becomes [1, 4, 2, 3]
Reverse subarray [4, 2], arr becomes [1, 2, 4, 3]
Reverse subarray [4, 3], arr becomes [1, 2, 3, 4]
There are multiple ways to convert arr to target, this is not the only way to do so.

### Example 2

**Input:**
target = [7]
arr = [7]

**Output:**
true

### Example 3

**Input:**
target = [3, 7, 9]
arr = [3, 7, 11]

**Output:**
false

```python
import collections
from typing import List

class Solution:
  def canBeEqual(self, target: List[int], arr: List[int]) -> bool:
    return collections.Counter(arr) == collections.Counter(target)
```

<h2>Time Complexity</h2>

The time complexity of the solution is O(n), where n is the length of the arrays. This is because creating a Counter object takes O(n) time and comparing two Counter objects also takes O(n) time.

<h2>Space Complexity</h2>

The space complexity of the solution is O(n) due to the storage used by the Counter objects.

<h2>Explanation</h2>

The problem can be solved by checking if both arrays contain the same elements with the same frequencies. This is because reversing subarrays only changes the order of elements, not their frequency. By using collections.Counter, we can easily compare the frequencies of elements in both arrays. If they match, we return true; otherwise, we return false.
