# Check for BST

Given the root of a binary tree, check whether it is a BST (Binary Search Tree) or not. Note that in this context, BSTs cannot contain duplicate nodes.<br>

# A BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.<br>
The right subtree of a node contains only nodes with keys greater than the node's key.<br>
Both the left and right subtrees must also be binary search trees.<br>
Example 1:<br>
Input:<br>

   2
 /    \
1      3<br>
Output: 1<br>

Explanation: The left subtree of the root node contains a node with a key lesser than the root node's key, and the right <br>subtree of the root node contains a node with a key greater than the root node's key. Hence, the tree is a BST.<br>

Example 2:<br>
Input:<br>


  2
   \
    7
     \
      6
       \
        5
         \
          9
           \
            2
             \
              6
Output: 0<br>

<h2>Explanation:</h2>
 Since the node with value 7 has right subtree nodes with keys less than 7, this is not a BST.<br>

<h2>Your Task:</h2>
You don't need to read input or print anything. Your task is to complete the function isBST() which takes the root of the tree as a parameter and returns true if the given binary tree is a BST, else returns false.

Expected Time Complexity: O(N).
Expected Auxiliary Space: O(Height of the BST).

```python
class Solution:
    def helper(self, root, min_range, max_range):
        if root is None:
            return True
            
        if min_range is not None and root.data <= min_range:
            return False
            
        if max_range is not None and root.data >= max_range:
            return False
            
        return self.helper(root.left, min_range, root.data) and \
               self.helper(root.right, root.data, max_range)
    
    def isBST(self, root):
        return self.helper(root, None, None)
```