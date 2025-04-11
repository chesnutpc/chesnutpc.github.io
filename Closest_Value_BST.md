---
layout: default
title: Closest Value BST
---

## Closest Value BST

### Question
Write a function that takes in a Binary Search Tree (BST) and a target integer value and returns the closest value to that target value contained in the BST.

You can assume that there will only be one closest value.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left and its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.

Sample Input:
tree = 10
      /  \
     5    15
    / \   / \
   2   5 13 22
  /         \
 1           14

target = 12

Sample Output:
13

Starter Code
```
# This is the class of the input tree. Do not edit.
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def findClosestValueInBst(tree, target):
    pass
```

### Solution
```
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def findClosestValueInBst(tree, target):
    return findClosestValueInBstHelper(tree, target, tree.value)

def findClosestValueInBstHelper(tree, target, closest):
    currNode = tree
    # We will take advantage of the BST property of every value
    # in the left-subtree being less than the current value and
    # every value in the right-subtree being greater than the
    # current value
    # First we determine is the current node's value is closer
    # to the target value than our stored value
    while currNode is not None:
        if abs(target - closest) > abs(target - currNode.value):
            closest = currNode.value
        # Next we decide if we should traverse left or right
        # If target is less than current node's value, we should go
        # left because all values in the right subtree are higher and
        # further away
        if target < currNode.value:
            currNode = currNode.left
        # If target is greater than current node's value, we should go
        # right to explore values that are greater than the current node's
        # value
        elif target > currNode.value:
            currNode = currNode.right
        # If target is equal to the current node's value, we can return
        else:
            break
    return closest
```
O(1) space - we only need 1 extra variable\
O(log(n)) time on average - you can elimate half the tree as you traverse
O(n) time in worst case when each not in tree has only one child

