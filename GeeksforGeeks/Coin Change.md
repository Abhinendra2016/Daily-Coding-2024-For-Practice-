# Problem: Coin Change

Given an integer array `coins` of size `N` representing different denominations of currency and an integer `sum`, find the number of ways you can make `sum` by using different combinations from `coins`.

## Example

Input: N = 3, sum = 4, coins = {1,2,3}
Output: 4
Explanation: Four Possible ways are: {1,1,1,1},{1,1,2},{2,2},{1,3}.

Input: N = 4, Sum = 10, coins = {2,5,3,6}
Output: 5
Explanation: Five Possible ways are: {2,2,2,2,2}, {2,2,3,3}, {2,2,6}, {2,3,5} and {5,5}.



## Solution

```python
class Solution:
    def count(self, coins, N, Sum):
        dp = [0] * (Sum + 1)
        dp[0] = 1  # There is one way to make a sum of 0, i.e., not choosing any coin.
        for coin in coins:
            for j in range(coin, Sum + 1):
                dp[j] += dp[j - coin]
        return dp[Sum]
```
## Approach

To find the number of ways to make a sum using different combinations of coins, we can use dynamic programming. We create a dp array where dp[i] represents the number of ways to make a sum of i using the coins. We initialize dp[0] to 1 because there is one way to make a sum of 0 (not choosing any coin). Then, for each coin, we update dp[j] for all j from coin to sum by adding dp[j - coin].