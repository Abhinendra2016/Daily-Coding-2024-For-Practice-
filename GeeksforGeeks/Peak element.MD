# Problem: Find Peak Element

Given an 0-indexed array of integers `arr[]` of size `n`, find its peak element and return its index. An element is considered a peak if its value is greater than or equal to the values of its adjacent elements (if they exist).

Note: The output will be 1 if the index returned by your function is correct; otherwise, it will be 0.

## Example

Input: 
n = 3
arr[] = {1, 2, 3}
Output: 
1
Explanation: 
If the index returned is 2, then the output printed will be 1. Since arr[2] = 3 is greater than its adjacent elements, and there is no element after it, we can consider it as a peak element. No other index satisfies the same property, so the answer will be printed as 0.

Input:
n = 7
arr[] = {1, 1, 1, 2, 1, 1, 1}
Output: 
1
Explanation: 
In this case, there are 5 peak elements with indices {0, 1, 3, 5, 6}. Returning any of them will give you the correct answer.


## Solution

```python
class Solution:
    def peakElement(self, arr, n):
        low = 0
        high = n - 1
        while low < high:
            mid = low + (high - low) // 2

            if arr[mid] > arr[mid + 1]:
                high = mid
            else:
                low = mid + 1
        return low
```
## Approach

To find the peak element in an array, we can use a binary search approach. We initialize two pointers, `low` and `high`, representing the start and end of the array, respectively. We then iterate until `low` is less than `high`.
<br>
- Calculate the middle index `mid` as `low + (high - low) // 2`.<br>
- Check if the element at index `mid` is greater than the element at index `mid + 1`. If it is, then the peak element must be on the left side of `mid`, so we set `high` to `mid`. Otherwise, the peak element must be on the right side of `mid`, so we set `low` to `mid + 1`.<br>

By the end of the iteration, `low` will point to the peak element, and we return `low` as the result.
