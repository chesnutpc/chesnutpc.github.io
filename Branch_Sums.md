---
layout: default
title: Branch Sums
---

## Branch Sums

### Question
Write a function that takes in a Binary Tree and returns a list of its branch sums ordered from leftmost branch sum to rightmost branch sum.

A branch sum is the sum of all values in a Binary Tree branch. A Binary Tree branch is a path of nodes in a tree that starts at the root node and ends at any leaf node.

Each BinaryTree node has an integer value, a left child node, and a right child node. Children nodes can either be BinaryTree nodes themselves or None / null.

Sample Input:
```
tree = 1
      / \
     2     3
    / \   / \
   4   5  6  7
  / \  /
 8   9 10

```
Sample Output:
```
[15, 16, 18, 10, 11]
// 15 == 1 + 2 + 4 + 8
// 16 == 1 + 2 + 4 + 9
// 18 == 1 + 2 + 5 + 10
// 10 == 1 + 3 + 6
// 11 == 1 + 3 + 7

```
Starter Code:
```
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def branchSums(root):
    pass
```

### Solution
```
# This is the class of the input root. Do not edit it.
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

# General strategy: Traverse the tree in a depth-first manner
# This will be done recursively, passing a running sum
# When you reach a leaf node, sum the value and the running sum
# and add it to the return list.

def branchSums(root):
    # Empty list to store branch sums
    sums = []
    # call helper function at the root node with running sum of 0
    calculateBranchSums(root, 0, sums)
    return sums

def calculateBranchSums(node, runningSum, sums):
    # Base case, return if node is none
    if node is None:
        return
    # Update runningSum by adding current node's value
    newRunningSum = runningSum + node.value
    # Check if current node is a leaf node
    if node.left is None and node.right is None:
        # append newRunningSum to sums list and return
        sums.append(newRunningSum)
        return
    # Recursively process the left subtree and right subtree
    calculateBranchSums(node.left, newRunningSum, sums)
    calculateBranchSums(node.right, newRunningSum, sums)
```
O(n) space in an unbalanced tree due to recursive calls for each node\
O(log(n)) space for a balanced tree because the call stack will be equal to the depth of the tree\
O(n) time to traverse the tree, constant time operations at each node
