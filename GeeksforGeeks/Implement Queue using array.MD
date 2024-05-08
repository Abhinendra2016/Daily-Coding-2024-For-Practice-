# Problem: Implement a Queue using an Array

Implement a Queue using an Array. Queries in the Queue are of the following type:
1. `1 x`: Push 'x' into the queue.
2. `2`: Pop element from the queue and print the popped element.

Example 1:
Input:
Q = 5
Queries = 1 2 1 3 2 1 4 2
Output: 2 3
Explanation:
In the first test case:
1 2: The queue will be {2}
1 3: The queue will be {2, 3}
2: Popped element will be 2, the queue will be {3}
1 4: The queue will be {3, 4}
2: Popped element will be 3

Example 2:
Input:
Q = 4
Queries = 1 3 2 2 1 4
Output: 3 -1
Explanation:
In the second test case:
1 3: The queue will be {3}
2: Popped element will be 3, the queue will be empty
2: There is no element in the queue, hence -1
1 4: The queue will be {4}

Your Task:
Complete the two methods `push(x)` which pushes an integer 'x' into the queue, and `pop()` which pops an integer from the queue and returns it. If the queue is empty, it should return -1.

Expected Time Complexity: O(1) for both `push()` and `pop()`.
Expected Auxiliary Space: O(1) for both `push()` and `pop()`.

## Solution

```python
class MyQueue:
    def __init__(self):
        self.queue = []

    # Function to push an element x in a queue.
    def push(self, x):
        self.queue.append(x)

    # Function to pop an element from queue and return that element.
    def pop(self):
        if self.queue:
            return self.queue.pop(0)
        else:
            return -1
```
## Approach

To implement a queue using an array, we can use a list in Python. We will use the `append` method to add elements to the end of the list (enqueue operation) and the `pop(0)` method to remove elements from the front of the list (dequeue operation). The `pop(0)` method removes and returns the first element of the list.<br>

- For the `push` method, we simply append the element to the end of the list.<br>
- For the `pop` method, we check if the list is empty. If it is not empty, we remove and return the first element of the list. If the list is empty, we return -1 to indicate that the queue is empty.<br>

Both `push` and `pop` operations have a time complexity of O(1) since appending to the end of a list and popping from the front of a list both have constant time complexity. The space complexity is also O(1) since we are using a fixed amount of space to store the queue elements.