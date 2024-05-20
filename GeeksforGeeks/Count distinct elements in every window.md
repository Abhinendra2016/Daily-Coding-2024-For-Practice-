# Count Distinct Elements in Every Window

Given an array of integers and a number K, find the count of distinct elements in every window of size K in the array.

### Example 1

Input:

- N = 7, K = 4
- A = [1, 2, 1, 3, 4, 2, 3]

Output:

- [3, 4, 4, 3]

Explanation:

- Window 1 of size k = 4 is [1, 2, 1, 3]. Number of distinct elements in this window is 3.
- Window 2 of size k = 4 is [2, 1, 3, 4]. Number of distinct elements in this window is 4.
- Window 3 of size k = 4 is [1, 3, 4, 2]. Number of distinct elements in this window is 4.
- Window 4 of size k = 4 is [3, 4, 2, 3]. Number of distinct elements in this window is 3.

### Example 2

Input:

- N = 3, K = 2
- A = [4, 1, 1]

Output:

- [2, 1]

## Solution

```python
from collections import Counter

class Solution:
    def countDistinct(self, A, N, K):
        # Initialize the counter with the first K elements
        cnt = Counter(A[:K])

        # Initialize the result list with the count of distinct elements in the first window
        res = []
        count = len(cnt)
        res.append(count)

        # Traverse the array starting from the Kth element to the end
        for i in range(K, N):
            # Add the new element of the current window
            cnt[A[i]] += 1

            # If the new element is unique, increment the count of distinct elements
            if cnt[A[i]] == 1:
                count += 1

            # Remove the element that is sliding out of the window
            cnt[A[i - K]] -= 1

            # If the element that slid out is no longer in the window, decrement the count of distinct elements
            if cnt[A[i - K]] == 0:
                count -= 1

            # Append the current count of distinct elements to the result list
            res.append(count)

        return res
```

<h2>Explanation</h2>

Initialization:
We use a counter (cnt) to keep track of the frequency of elements in the current window of size K.<br>
The initial window is the first K elements of the array.<br>
We initialize the result list (res) with the count of distinct elements in the first window.<br>
Sliding Window:<br>
We iterate through the array starting from the Kth element to the end.<br>
For each element, we:<br>
Add the new element to the counter.<br>
If this new element is unique (i.e., appears for the first time in the window), we increment the count of distinct elements.
Remove the element that is sliding out of the window from the counter.<br>
If the element that slid out is no longer in the window, we decrement the count of distinct elements.<br>
Append the current count of distinct elements to the result list.<br>

<h2>Time Complexity</h2>

O(N): We traverse the array once and each operation (addition/removal in the counter) is O(1).<br>

<h2>Space Complexity</h2>

O(K): The space used by the counter to store at most K elements at any given time.<br>
