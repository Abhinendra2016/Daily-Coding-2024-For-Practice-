# Problem: Combination Sum II

Given an array of integers `arr`, the length of the array `n`, and an integer `k`, find all the unique combinations in `arr` where the sum of the combination is equal to `k`. Each number can only be used once in a combination. Return the combinations in the lexicographically sorted order, where each combination is in non-decreasing order.

## Example

Input: 
n = 5, k = 7
arr[] = {1, 2, 3, 3, 5}
Output:
{{1, 3, 3}, {2, 5}}
Explanation:
1 + 3 + 3 = 7
2 + 5 = 7

Input:
n = 6, k = 30
arr[] = {5, 10, 15, 20, 25, 30}
Output:
{{5, 10, 15}, {5, 25}, {10, 20}, {30}}
Explanation:
5 + 10 + 15 = 30
5 + 25 = 30
10 + 20 = 30

## Solution

```python
class Solution:
    def CombinationSum2(self, arr, n, k):
        res = []
        arr.sort()

        def dfs(idx, sumi, path, res):
            if sumi == k:
                res.append(path)
            if sumi > k:
                return
            for i in range(idx, len(arr)):
                if i > idx and arr[i] == arr[i - 1]:
                    continue
                dfs(i + 1, sumi + arr[i], path + [arr[i]], res)

        dfs(0, 0, [], res)
        return res
```
<h2>Explanation</h2>

We first sort the array arr to ensure that duplicate elements are grouped together.<br>
We define a recursive function dfs that explores all possible combinations.<br>
The function dfs takes four parameters: idx (current index), sumi (current sum), path (current path of elements), and res (result list to store valid combinations).<br>
If the current sum equals k, we append the current path to the result list.<br>
If the current sum exceeds k, we return without further exploration.<br>
We iterate over the array from the current index onwards, skipping duplicates to avoid duplicate combinations.<br>
For each element, we recursively call dfs with the updated index, sum, and path.<br>
Finally, we call dfs with initial values and return the result list.<br>