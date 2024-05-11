# Problem: Sum of Infinite Array

Given an array “A” of N integers and a new array “B” as the concatenation of array “A” for an infinite number of times, you are given Q queries, each consisting of two integers “L“ and “R” (1-based indexing). Your task is to find the sum of the subarray from index “L” to “R” (both inclusive) in the infinite array “B” for each query. Return the answer as modulus 10^9+7.

## Example

Input: arr = [1, 2, 3], n = 3, queries = [(1, 5), (2, 6)], q = 2
Output: [14, 15]
Explanation:
The infinite array B is [1, 2, 3, 1, 2, 3, ...].
For the first query (1, 5), the subarray is [1, 2, 3, 1, 2] with a sum of 9.
For the second query (2, 6), the subarray is [2, 3, 1, 2, 3] with a sum of 12.

## Solution

```python
def sumInRanges(arr, n, queries, q):
    mod = 10**9 + 7

    def get_sum(sumArray, x, n):
        count = (x // n) % mod
        remain = (x % n) % mod
        ansi = (count * sumArray[n] + sumArray[remain]) % mod
        return ansi

    ans = []
    sumArray = [0] * (n + 1)
    for i in range(1, n + 1):
        sumArray[i] = (sumArray[i - 1] + arr[i - 1]) % mod

    for query in queries:
        l, r = query
        rsum = get_sum(sumArray, r, n)
        lsum = get_sum(sumArray, l - 1, n)
        ans.append((rsum - lsum + mod) % mod)

    return ans

```

<h2>Time Complexity</h2>

The time complexity of this solution is O(n + q), where n is the size of the input array arr and q is the number of queries. This is because we pre-calculate the prefix sum of arr in O(n) time and then process each query in O(1) time.<br>

<h2>Space Complexity</h2>

The space complexity of this solution is O(n), where n is the size of the input array arr. This is because we store the prefix sum of arr in the sumArray list.<br>

<h2>Explanation</h2>

We first calculate the prefix sum of the array arr.<br>
We define a function get_sum to calculate the sum of elements in the subarray [l, r] of the infinite array B.<br>
For each query, we calculate the sum of elements in the subarray [l, r] using the get_sum function and append it to the answer list ans.
