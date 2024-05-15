# Problem: Positive Negative Pair

Given an array of distinct integers, find all the pairs having a positive value and negative value of a number that exists in the array. Return the pairs in any order.

Note:
The pair consists of equal absolute values, one being positive and another negative.

Return an empty array if no such pair exists.

## Solution

```python
from collections import defaultdict

def pairs(arr, n):
    negativeValues = {}
    pairArr = []

    for i in arr:
        if i < 0:
            negativeValues[i] = 1

    for i in arr:
        if i > 0 and -i in negativeValues:
            pairArr.append([-i, i])

    return pairArr
```
<h2>Explanation</h2>

We first iterate through the array to identify all negative values and store them in a dictionary for quick lookup.<br>
Then, we iterate through the array again and check if the current element is positive and its negative counterpart exists in the dictionary.<br>
If such a pair is found, we add it to the pairArr.<br>
Finally, we return the array containing all the positive-negative pairs<br>