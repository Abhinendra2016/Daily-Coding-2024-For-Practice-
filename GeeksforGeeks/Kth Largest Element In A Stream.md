# Problem: Kth Largest Element In A Stream

You will be given a stream of numbers, and you need to find the 'kth' largest number in the stream at any given time.

As the stream of numbers cannot be given during compile time, you need to design a data structure that can accept infinite numbers and return the 'kth' largest number at any given time.

The stream of numbers is a large collection of numbers from which integers are read at runtime. The user will never know the upper limit on the number of integers that will be read.

The implemented data structure must support the following operations:

1. `add(DATA)`:
   - This function should take one argument of type integer and store it in its pool.
   - It returns the 'kth' largest number from the current pool of integers.

You will be given 'q' queries:

- `val`: For this query, insert the integer into your current pool of integers and return the 'kth' largest integer from the existing pool of integers.

### Note
1. The maximum number of integers that will be given will always be under memory limits.
2. You will also be given an initial pool of integers whose size equals k.
3. The maximum number of queries will be less than 10^5.
4. The 'kth' largest element is not the 'kth' distinct element but the 'kth' largest element in the sorted order.
5. There will be at least one query of type 2.

## Example 1

**Sample Input 1:**
2 3
2 1 3
3
5
**Sample Output 1:**
2
3
**Explanation:**
The initial pool is - 2, 1, 3. 

When 3 is added, the pool is now 3, 2, 1, 3. The 3rd largest element is 2 (when we sort the pool, it becomes 3, 3, 2, 1).

When 5 is added, the pool is now 5, 3, 2, 1, 3. The 3rd largest element is 3 (when we sort the pool, it becomes 5, 3, 3, 2, 1).


## Constraints

- 1 <= Q <= 10^4
- 1 <= K <= 10^5
- 1 <= DATA <= 10^9 

### Time Limit: 1 sec

## Solution

```python
from typing import List
import heapq

class KthLargest:
    def __init__(self, k: int, arr: List[int]):
        self.min_heap = arr
        self.k = k
        heapq.heapify(self.min_heap)

    def add(self, num: int) -> int:
        heapq.heappush(self.min_heap, num)
        if len(self.min_heap) > self.k:
            heapq.heappop(self.min_heap)
        return self.min_heap[0]
```