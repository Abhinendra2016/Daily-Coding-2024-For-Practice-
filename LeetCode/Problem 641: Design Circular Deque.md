# Problem 641: Design Circular Deque
Design your implementation of the circular double-ended queue (deque).

Implement the `MyCircularDeque` class:

- `MyCircularDeque(int k)` Initializes the deque with a maximum size of `k`.
- `boolean insertFront()` Adds an item at the front of Deque. Returns `true` if the operation is successful, or `false` otherwise.
- `boolean insertLast()` Adds an item at the rear of Deque. Returns `true` if the operation is successful, or `false` otherwise.
- `boolean deleteFront()` Deletes an item from the front of Deque. Returns `true` if the operation is successful, or `false` otherwise.
- `boolean deleteLast()` Deletes an item from the rear of Deque. Returns `true` if the operation is successful, or `false` otherwise.
- `int getFront()` Returns the front item from the Deque. Returns `-1` if the deque is empty.
- `int getRear()` Returns the last item from Deque. Returns `-1` if the deque is empty.
- `boolean isEmpty()` Returns `true` if the deque is empty, or `false` otherwise.
- `boolean isFull()` Returns `true` if the deque is full, or `false` otherwise.

### Example 1:

# Input:
["MyCircularDeque", "insertLast", "insertLast", "insertFront", "insertFront", "getRear", "isFull", "deleteLast", "insertFront", "getFront"]
[[3], [1], [2], [3], [4], [], [], [], [4], []]

 # Output:
[null, true, true, true, false, 2, true, true, true, 4]
Explanation:
MyCircularDeque myCircularDeque = new MyCircularDeque(3);
myCircularDeque.insertLast(1);  // return True
myCircularDeque.insertLast(2);  // return True
myCircularDeque.insertFront(3); // return True
myCircularDeque.insertFront(4); // return False, the queue is full.
myCircularDeque.getRear();      // return 2
myCircularDeque.isFull();       // return True
myCircularDeque.deleteLast();   // return True
myCircularDeque.insertFront(4); // return True
myCircularDeque.getFront();     // return 4
# Constraints:
1 <= k <= 1000
0 <= value <= 1000
At most 2000 calls will be made to insertFront, insertLast, deleteFront, deleteLast, getFront, getRear, isEmpty, and isFull.


```python
class MyCircularDeque:
    def __init__(self, k: int):
        self.queue = [0] * k
        self.head = 0
        self.size = 0
        self.capacity = k

    def insertFront(self, value: int) -> bool:
        if self.isFull():
            return False
        if not self.isEmpty():
            self.head = (self.head - 1 + self.capacity) % self.capacity
        self.queue[self.head] = value
        self.size += 1
        return True

    def insertLast(self, value: int) -> bool:
        if self.isFull():
            return False
        tail_index = (self.head + self.size) % self.capacity
        self.queue[tail_index] = value
        self.size += 1
        return True

    def deleteFront(self) -> bool:
        if self.isEmpty():
            return False
        self.head = (self.head + 1) % self.capacity
        self.size -= 1
        return True

    def deleteLast(self) -> bool:
        if self.isEmpty():
            return False
        self.size -= 1
        return True

    def getFront(self) -> int:
        if self.isEmpty():
            return -1
        return self.queue[self.head]

    def getRear(self) -> int:
        if self.isEmpty():
            return -1
        tail_index = (self.head + self.size - 1) % self.capacity
        return self.queue[tail_index]

    def isEmpty(self) -> bool:
        return self.size == 0

    def isFull(self) -> bool:
        return self.size == self.capacity
```
<h2>Time Complexity</h2>

insertFront(), insertLast(), deleteFront(), and deleteLast() have a time complexity of O(1) because only a few pointer manipulations are required.
getFront(), getRear(), isEmpty(), and isFull() also have a time complexity of O(1) as they just check conditions or return specific values.<br>
<h2>Space Complexity</h2>

The space complexity is O(k) where k is the capacity of the deque. The array used to store the deque's values takes up space proportional to k.