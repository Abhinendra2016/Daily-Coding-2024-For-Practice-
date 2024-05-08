# Problem: Binary Search

Given a sorted array of size `N` and an integer `K`, find the position (0-based indexing) at which `K` is present in the array using binary search.

## Example

Input:
N = 5
arr[] = {1, 2, 3, 4, 5}
K = 4
Output: 3
Explanation: 4 appears at index 3.

Input:
N = 5
arr[] = {11, 22, 33, 44, 55}
K = 445
Output: -1
Explanation: 445 is not present.



## Solution

```python
class Solution:
    def binarysearch(self, arr, n, k):
        low = 0
        high = n - 1
        while low <= high:
            mid = (low + high) // 2
            if arr[mid] == k:
                return mid
            elif arr[mid] < k:
                low = mid + 1
            else:
                high = mid - 1
        return -1
```
## Approach

To find the position of `K` in a sorted array using binary search, we can follow these steps:<br>

- Initialize `low` to 0 and `high` to `N - 1`.<br>
- While `low` is less than or equal to `high`, do the following:<br>
  - Calculate `mid` as `(low + high) // 2`.<br>
  - If `arr[mid]` is equal to `K`, return `mid`.<br>
  - If `arr[mid]` is less than `K`, set `low = mid + 1`.<br>
  - If `arr[mid]` is greater than `K`, set `high = mid - 1`.<br>
- If `K` is not found in the array, return -1.