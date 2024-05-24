# Problem: Alternate Positive and Negative Numbers

Given an unsorted array `Arr` of `N` positive and negative numbers, your task is to create an array of alternate positive and negative numbers without changing the relative order of positive and negative numbers.

**Note:** The array should start with a positive number and `0` (zero) should be considered a positive element.

## Examples:

**Example 1:**

**Input:**
N = 9  
Arr[] = {9, 4, -2, -1, 5, 0, -5, -3, 2}

**Output:**
9 -2 4 -1 5 -5 0 -3 2

**Explanation:**
Positive elements: 9, 4, 5, 0, 2  
Negative elements: -2, -1, -5, -3  
As we need to maintain the relative order of positive elements and negative elements, we will pick each element from the positive and negative lists and store them alternately. If any of the positive and negative numbers are exhausted, we will continue with the remaining elements. The output is 9, -2, 4, -1, 5, -5, 0, -3, 2.

**Example 2:**

**Input:**
N = 10  
Arr[] = {-5, -2, 5, 2, 4, 7, 1, 8, 0, -8}

**Output:**
5 -5 2 -2 4 -8 7 1 8 0

**Explanation:**
Positive elements: 5, 2, 4, 7, 1, 8, 0  
Negative elements: -5, -2, -8  
As we need to maintain the relative order of positive elements and negative elements, we will pick each element from the positive and negative lists and store them alternately. If any of the positive and negative numbers are exhausted, we will continue with the remaining elements. The output is 5, -5, 2, -2, 4, -8, 7, 1, 8, 0.

## Constraints:

1 ≤ N ≤ 10^7  
-10^6 ≤ Arr[i] ≤ 10^7

## Solution

```python
from itertools import zip_longest

class Solution:
    def rearrange(self, arr, n):
        pos = [num for num in arr if num >= 0]
        neg = [num for num in arr if num < 0]
        res = []
        i = 0
        for p, n in zip_longest(pos, neg, fillvalue=None):
            if p is not None:
                arr[i] = p
                i += 1
            if n is not None:
                arr[i] = n
                i += 1
        return arr
```

<h2>Time Complexity</h2>
The time complexity of this solution is O(N), where N is the length of the input array. This is because we iterate through the array to separate positive and negative numbers and then iterate again to rearrange them.
<h2>Space Complexity</h2>
The space complexity of this solution is O(N), where N is the length of the input array
<h2>Explanation</h2>
The solution follows these steps:<br>
1. Separate the input array into two lists: `pos` for positive numbers (including zero) and `neg` for negative numbers.<br>
2. Use `zip_longest` from `itertools` to alternately pick elements from `pos` and `neg` and place them back into the original array.
3. If one of the lists is<br>