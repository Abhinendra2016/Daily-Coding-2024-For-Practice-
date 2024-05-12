# Problem: 0-1 Knapsack

A thief is robbing a store and can carry a maximum weight of ‘W’ into his knapsack. There are 'N' items available in the store and the weight and value of each item are known to the thief. Considering the constraints of the maximum weight that a knapsack can carry, you have to find the maximum profit that a thief can generate by stealing items.

Note: The thief is not allowed to break the items.

For example, N = 4, W = 10 and the weights and values of items are weights = [6, 1, 5, 3] and values = [3, 6, 1, 4]. Then the best way to fill the knapsack is to choose items with weights 6, 1, and 3. The total value of the knapsack = 3 + 6 + 4 = 13.

## Solution

```python
def maxProfit(values, weights, n, w):
    def memoization(idx, w, dp):
        if idx < 0 or w <= 0:
            return 0

        if dp[idx][w] != -1:
            return dp[idx][w]

        not_take = 0 + memoization(idx - 1, w, dp)

        take = float('-inf')
        if weights[idx] <= w:
            take = values[idx] + memoization(idx - 1, w - weights[idx], dp)

        dp[idx][w] = max(not_take, take)
        return dp[idx][w]

    def tabulation():
        dp = [[0] * (w + 1) for _ in range(n + 1)]

        for idx in range(1, n + 1):
            for W in range(1, w + 1):
                not_take = dp[idx - 1][W]

                take = 0
                if weights[idx - 1] <= W:
                    take = values[idx - 1] + dp[idx - 1][W - weights[idx - 1]]

                dp[idx][W] = max(not_take, take)

        return dp[n][w]

    return tabulation()
```
<h2>Explanation</h2>

The maxProfit function calculates the maximum profit that can be achieved by the thief using either the memoization or tabulation approach.<br>
The memoization function uses recursion and memoization to find the maximum profit. It keeps track of the maximum profit for each item and weight combination in a 2D dp array.<br>
The tabulation function uses a bottom-up approach to fill the dp array iteratively.<br>
The function returns the maximum profit calculated using the tabulation approach.<br>