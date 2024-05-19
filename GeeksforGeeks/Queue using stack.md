# Queue using Stack

Implement a Queue using two stacks `s1` and `s2`.

### Examples

**Example 1:**

Input:
enqueue(2)
enqueue(3)
dequeue()
enqueue(4)
dequeue()

### Constraints

- 1 <= Number of queries <= 100
- 1 <= values of the stack <= 100

## Solution

```python
class Queue:
    def __init__(self):
        self.s1 = []
        self.s2 = []

    def enqueue(self, x):
        self.s1.append(x)

    def dequeue(self):
        # Reverse the sequence from s1 to s2
        while self.s1:
            self.s2.append(self.s1.pop())

        # Store the result
        result = self.s2.pop() if self.s2 else -1

        # Set it back to original sequence
        while self.s2:
            self.s1.append(self.s2.pop())

        return result
```

<h2>Explanation</h2>

This implementation uses two stacks to create a queue. The enqueue operation is straightforward and simply pushes an element onto the first stack (s1). The dequeue operation is more involved:<br>

Transfer all elements from s1 to s2. This reverses the order of the elements.<br>
Pop the top element from s2, which is the oldest element added to s1, mimicking the dequeue operation of a queue.<br>
Transfer the remaining elements back from s2 to s1 to restore the original order<br>
