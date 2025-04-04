---
layout: default
title: Sum of Node Depths
---

## Sum of Node Depths

### Question
The distance between a node in a binary tree and the tree's root is the node depth.  Write a function that takes a binary tree and returns the sum of its nodes' depths.

Sample Input:
```
tree = 1
      / \
     2     3
    / \   / \
   4   5  6  7
  / \ 
 8   9

```
Sample Output:
```
16
// The dpth of the node with value 2 is 1
// The dpth of the node with value 3 is 1
// The dpth of the node with value 4 is 2
// ...
// Summing all the depths yields 16
```
Starter Code:
```
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def nodeDepths(root):
    pass
```

### Solution
```
# This is the class of the input binary tree.
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

# We will again traverse the tree recursively
# At each node at its depth to depthSum
def nodeDepths(root, depthSum = 0):
    # Base case, node is none return 0
    if root is None:
        return 0
    # otherwise, traverse left and right subtrees
    # adding to depthSum
    return depthSum + nodeDepths(root.left, depthSum + 1) + nodeDepths(root.right, depthSum + 1)
```
O(n) space in an unbalanced tree due to recursive calls for each node\
O(log(n)) space for a balanced tree because the call stack will be equal to the depth of the tree\
O(n) time to traverse the tree, constant time operations at each node
