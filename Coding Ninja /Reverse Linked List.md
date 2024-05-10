# Problem: Reverse Linked List

Given a singly linked list of integers. Your task is to return the head of the reversed linked list.

For example:
The given linked list is 1 -> 2 -> 3 -> 4-> NULL. Then the reverse linked list is 4 -> 3 -> 2 -> 1 -> NULL and the head of the reversed linked list will be 4.

## Solution

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

def reverseLinkedList(head):
    itr = head
    dnode = Node(-1)
    temp = dnode
    while(itr):

        next_node = itr.next
        itr.next = temp.next
        temp.next = itr
        itr = next_node
    return dnode.next
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the number of nodes in the linked list. This is because we iterate through the entire linked list once to reverse it.

<h2>Space Complexity</h2>

The space complexity of this solution is O(1), as we use only a constant amount of extra space, regardless of the size of the input linked list. We do not use any additional data structures that grow with the size of the input.

<h2>Explanation</h2>

We initialize dnode as a dummy node to which we'll attach the reversed linked list.<br>
We iterate through the original linked list (itr) and at each step, we detach the current node from the original linked list and attach it to the dnode (which is the head of the reversed linked list).<br>
Finally, we return the head of the reversed linked list (dnode.next).