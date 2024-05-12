# Problem: Cut Logs

Ninja is a log cutter. He has a ‘K’ number of axes and an infinite amount of logs. But, Ninja has a log cutting stand that has a capacity of ‘N’, which means he can only try to cut at max ‘N’ logs in one go. All the axes are exactly the same and can cut up to some logs in one go. If we try to cut more logs than its capacity the axe will break.

To improve efficiency, Ninja wants to know how many logs he can cut with an axe in one go without breaking it. But, he wants to know this is the minimum number of moves and in the allotted number of axes.

## Example

Let the number of axes (K) be 2 & the capacity of the log cutting stand (N) be 6.

From the above example, we can see that the maximum number of moves is 3 for 2 axes and a capacity of 6 logs.

## Constraints
- 1 <= T <= 10
- 1 <= K <= 100
- 1 <= N <= 10000

## Solution

```python
def memoization(e, f, dp):
    # Base cases
    if f <= 1 or e == 1:
        return f

    if dp[e][f] != -1:
        return dp[e][f]

    # Use binary search
    ans = float('inf')
    start, end = 1, f
    while start <= end:
        mid = (start + end) // 2

        BREAK = memoization(e - 1, mid - 1, dp)
        SURVIVE = memoization(e, f - mid, dp)

        # Update answer with minimum value
        ans = min(ans, 1 + max(BREAK, SURVIVE))

        if BREAK < SURVIVE:
            start = mid + 1
        else:
            end = mid - 1

    dp[e][f] = ans
    return ans

def cutLogs(k, n):
    dp = [[-1] * (n + 1) for _ in range(k + 1)]
    return memoization(k, n, dp)
```
## Explanation
- For test case 1: Refer to the example explained above.<br>
- For test case 2:<br>
    - First, try to cut 2 logs:<br>
        - If it cuts 2 logs, try to cut 3 logs.<br>
        - If it couldn’t cut 2 logs, try to cut 1 log.<br>
    - Thus, the maximum number of moves required are 3.<br>
