# Path In A Tree

## Problem Statement
You are given a binary tree with ‘N’ number of nodes and a node ‘X’. Your task is to print the path from the root node to the given node ‘X’.

A binary tree is a hierarchical data structure in which each node has at most two children.

## Solution
```python
from typing import List

class TreeNode:   
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def pathInATree(root: TreeNode, x: int) -> List[int]:
    l = []

    def find(root, x, l1):
        if root is None:
            return

        if root.data == x:
            l1.append(x)
            l.extend(l1)
            return

        if root.left:
            find(root.left, x, l1 + [root.data])

        if root.right:
            find(root.right, x, l1 + [root.data])

    find(root, x, [])

    if not l:
        return []
    else:
        return l
```
