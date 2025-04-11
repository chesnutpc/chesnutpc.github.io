---
layout: default
title: Closest Value BST
---

## Closest Value BST

### Question
Write a function that takes in a potentially invalid Binary Search Tree (BST) and returns a boolean representing whether the BST is valid.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left and its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.

A BST is valid if and only if all of its nodes are valid BST nodes.

Sample Input:
tree = 10
      /  \
     5    15
    / \   / \
   2   5 13 22
  /         \
 1           14

Sample Output:
true

Starter Code
```
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None


def validateBst(tree):
    pass
```

### Solution
```
# This is an input class. Do not edit.
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None


# We will recursively validate that a parent and it's potential two child
# nodes make up a valid BST.  This will be done in a depth-first search
# manner.  We also need to keep track of the range of acceptable values
# as we go deeper in to the tree.

def validateBst(tree):
    return validateBstHelper(tree, float("-inf"), float("inf"))

def validateBstHelper(tree, minValue, maxValue):
    # Base case: empty tree is valid
    if tree is None:
        return True
    # Check if current node's value is within acceptable range
    if tree.value < minValue or tree.value >= maxValue:
        return False
    # Recursively validate the left subtree
    # The left subtree's values should be less than the current node's val
    leftIsValid = validateBstHelper(tree.left, minValue, tree.value)

    # Recursively validate the left subtree
    # The right subtree's values should be greater than or equal to 
    # the current node's value
    rightIsValid = validateBstHelper(tree.right, tree.value, maxValue)

    # Return true is both subtrees are valid, false otherwise
    return leftIsValid and rightIsValid
```

O(h) space - we recursively call validateBstHelper, so the stack grows to the height of the tree\
O(n) time - we need to visit each node
