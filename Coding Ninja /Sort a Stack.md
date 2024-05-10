# Problem: Sort a Stack

You’re given a stack consisting of 'N' integers. Your task is to sort this stack in descending order using recursion.

We can only use the following functions on this stack S.

- `is_empty(S)`: Tests whether stack is empty or not.
- `push(S)`: Adds a new element to the stack.
- `pop(S)`: Removes the top element from the stack.
- `top(S)`: Returns the value of the top element. Note that this function does not remove elements from the stack.

**Constraints:**
1) Use of any loop constructs like while, for..etc is not allowed.
2) The stack may contain duplicate integers.
3) The stack may contain any integer i.e it may either be negative, positive, or zero.

## Solution

```python
def pop(stack):
    stack.pop()

def push(stack, element):
    stack.append(element)

def top(stack):
    return stack[-1]

def is_empty(stack):
    return len(stack) == 0

def sort(stack, lastIndex):
    if lastIndex == 0:
        return 
    temp = top(stack)
    pop(stack)
    sort(stack, lastIndex - 1)
    insert(stack, temp)

def insert(stack, temp):
    if is_empty(stack) or top(stack) <= temp:
        push(stack, temp)
        return
    last_val = top(stack)
    pop(stack)
    insert(stack, temp)
    push(stack, last_val)

def sortStack(stack):
    sort(stack, len(stack) - 1)
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n^2), where n is the number of elements in the stack. This is because for each element in the stack, we potentially have to compare it with all the elements in the stack to find its correct position.

<h2>Space Complexity</h2>

The space complexity of this solution is O(n), where n is the number of elements in the stack. This is because we use recursion, which requires additional space on the call stack proportional to the number of elements in the stack.


<h2>Explanation</h2>

The sort function recursively sorts the stack by popping each element, sorting the remaining stack, and then inserting the popped element back into the stack at the correct position using the insert function.<br>
The insert function recursively inserts the given element into the stack at the correct position by popping elements from the stack and comparing them with the given element until a suitable position is found.<br>
The sortStack function is the entry point for sorting the stack and calls the sort function with the index of the last element in the stack.