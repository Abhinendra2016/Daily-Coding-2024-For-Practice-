# Problem: Reverse a Linked List

Given a linked list of `N` nodes, the task is to reverse this list.

## Example 1:

**Input:**  
LinkedList: `1->2->3->4->5->6`  
**Output:** `6 5 4 3 2 1`  
**Explanation:** After reversing the list, elements are `6->5->4->3->2->1`.

## Example 2:

**Input:**  
LinkedList: `2->7->8->9->10`  
**Output:** `10 9 8 7 2`  
**Explanation:** After reversing the list, elements are `10->9->8->7->2`.

## Your Task:

The task is to complete the function `reverseList()` with `head` reference as the only argument and should return new head after reversing the list.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

**Constraints:**  
`1 <= N <= 10^4`

## Solution

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        prev = None
        current = head
        
        while current is not None:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
        
        return prev
```


<h2>Explanation</h2>

The problem requires reversing a singly linked list. The solution uses an iterative approach to reverse the list by modifying the pointers of each node.<br>

Initialize prev as None and current as the head of the list.<br>
Iterate through the list:<br>
Store the next node in next_node.<br>
Reverse the current node's pointer to point to prev.<br>
Move prev and current one step forward.<br>
After the loop, prev will be the new head of the reversed list.<br>
Return prev as the new head.<br>