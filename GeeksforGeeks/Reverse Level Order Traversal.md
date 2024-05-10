# Problem: Reverse Level Order Traversal

Given a binary tree of size n, find its reverse level order traversal. ie- the traversal must begin from the last level.
<br>
Example 1:
<br>
Input:
        1
      /   \
     3     2
<br>
Output: 
3 2 1
Explanation:<br>
Traversing level 1 : 3 2
Traversing level 0 : 1
<br>
Example 2:
<br>
Input:
       10
      /  \
     20   30
    / \ 
   40  60
<br>
Output: 
40 60 20 30 10
Explanation:
Traversing level 2 : 40 60
Traversing level 1 : 20 30
Traversing level 0 : 10<br>
<br>
Your Task: <br>
You don't need to read input or print anything. Complete the function reverseLevelOrder() which takes the root of the tree as input parameter and returns a list containing the reverse level order traversal of the given tree.

## Solution

```python
from collections import deque

def reverseLevelOrder(root):
    ans = deque()
    q = deque()
    q.append(root)
    while q:
        node = q.popleft()
        ans.appendleft(node.data)
        if node.right:
            q.append(node.right)
        if node.left:
            q.append(node.left)
    return ans
```
<h2>Explanation</h2>

We use a deque q to perform a level-order traversal of the tree, starting from the root.<br>
At each level, we append the node's value to the left side of the deque ans, effectively reversing the order.<br>
Finally, we return the deque ans, which contains the reverse level order traversal of the tree.<br>
The time complexity of this solution is O(n), where n is the number of nodes in the tree, as we visit each node exactly once. <br> The space complexity is also O(n) for the same reason.