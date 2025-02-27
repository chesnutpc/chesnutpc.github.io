---
layout: default
title: Min Heap Implementation
---

## Min Heap Implementation

### Question
Implement a minimum heap.  It should support the following methods.
1. buildHeap: Takes an array and sorts it into a minimum heap (in place). Call the siftDown method on every parent node starting with the last.
2. siftDown: Continuously swap a parent node with its smallest child node until the parent node is <= the child node
3. siftUp: Continuously swap a child node with its parent node until the parent node is <= the child node
4. Insert: Place the number at the end of the array and siftUp
5. Remove: Swap the first and last elements, pop the last element, siftDown the first element

### Hint
Array structure of a heap:
currentNode -> i
childOne -> 2i + 1
childTwo -> 2i + 2
parentNode -> floor((i - 1) / 2)

### Starter Code
```
class MinHeap:
    def __init__(self, array):
        # Do not edit the line below.
        self.heap = self.buildHeap(array)

    def buildHeap(self, array): # O(N) time
        # Write your code here.
        pass

    def siftDown(self): # O(log(N)) time
        # Write your code here.
        pass

    def siftUp(self): # O(log(N)) time
        # Write your code here.
        pass

    def peek(self):
        # Write your code here.
        pass

    def remove(self): # O(log(N)) time
        # Write your code here.
        pass

    def insert(self, value): # O(log(N)) time
        # Write your code here.
        pass
```

### Solution
