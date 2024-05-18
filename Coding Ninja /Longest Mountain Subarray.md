# Longest Mountain Subarray

You are given an array of 'N' integers denoting the heights of the mountains. You need to find the length of the longest subarray which has the shape of a mountain.

A mountain subarray is defined as a subarray which consists of elements that are initially in ascending order until a peak element is reached and beyond the peak element all other elements of the subarray are in decreasing order.

### Example

**Example 1:**

If the given array is: `[1, 3, 1, 4]`. The longest mountain subarray would be 3. This is because the longest mountain is `[1, 3, 1]` having length 3.

## Solution

```python
def longestMountain(arr, n):
    if n < 3:
        return 0
    ans = 0
    for i in range(1, n - 1):
        if arr[i] > arr[i - 1] and arr[i] > arr[i + 1]:
            count = 1
            j = i
            k = i

            while j > 0 and arr[j] > arr[j - 1]:
                j -= 1
                count += 1

            while k < n - 1 and arr[k] > arr[k + 1]:
                k += 1
                count += 1

            ans = max(ans, count)
    return ans
```
<h2>Time Complexity</h2>
The time complexity of this solution is O(n^2), where n is the number of elements in the 'arr array.<br>
This is because, for each peak element, the solution explores both the left and right sides to determine the length of the mountain.<br>
<h2>Space Complexity</h2>
The space complexity of this solution is O(1) since it uses a constant amount of extra space regardless of the input size.<br>
<h2>Explanation</h2>
The solution iterates through the array to find potential peaks, i.e., elements that are greater than their neighbors.<br>
 For each peak found, it expands outwards to the left and right to determine the length of the mountain. <br>The length of each mountain is tracked, and the maximum length found is returned as the result. If the array has less than 3 elements, it's impossible to form a mountain, and the function returns O.