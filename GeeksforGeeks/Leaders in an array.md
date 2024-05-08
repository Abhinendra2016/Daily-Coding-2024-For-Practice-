# Problem: Leaders in an array

Given an array A of positive integers. Your task is to find the leaders in the array. An element of the array is a leader if it is greater than or equal to all the elements to its right side. The rightmost element is always a leader.

## Example

Input:
n = 6
A[] = {16, 17, 4, 3, 5, 2}
Output: 17 5 2
Explanation: The first leader is 17 as it is greater than all the elements to its right. Similarly, the next leader is 5. The rightmost element is always a leader, so it is also included.

Input:
n = 5
A[] = {1, 2, 3, 4, 0}
Output: 4 0
Explanation: 0 is the rightmost element and 4 is the only element which is greater than all the elements to its right.

## Solution

```python
class Solution:
    # Function to find the leaders in the array.
    def leaders(self, A, N):
        leader = A[N - 1]
        ans = []
        ans.append(A[N - 1])
        count = 1
        for i in range(N - 2, -1, -1):
            if A[i] >= leader:
                ans.append(A[i])
                leader = A[i]
                count += 1
        result = []
        for i in range(count - 1, -1, -1):
            result.append(ans[i])
        return result
```
## Approach

To find the leaders in the array, we can start from the rightmost element and keep track of the maximum element found so far (initialized as the rightmost element). If we encounter an element greater than or equal to the maximum element found so far, we add it to the list of leaders and update the maximum element. We repeat this process for all elements from right to left.
