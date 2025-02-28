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
```
class MinHeap:
    def __init__(self, array):
        # Do not edit the line below.
        self.heap = self.buildHeap(array)

    def buildHeap(self, array):
        # Write your code here.
        pass

    def siftDown(self, currIdx, endIdx, heap):
        # Calculate the 1st child index (even if it does exist)
        childOneIdx = currIdx * 2 + 1
        # While that child exists
        while childOneIdx <= endIdx:
            # Calculate the 2nd child or set to -1 if it does not exist
            if currIdx * 2 + 2 <= endIdx:
                childTwoIdx = currIdx * 2 + 2
            else:
                childTwoIdx = -1
            # if child two exists and is less than child one
            if childTwoIdx != -1 and heap[childTwoIdx] < heap[childOneIdx]:
                # compare curr node to child two
                potentialSwapIdx = childTwoIdx
            else:
                # else we compare curr node to child one
                potentialSwapIdx = childOneIdx

            # if the child is smaller than the curr node, swap them
            if heap[potentialSwapIdx] < heap[currIdx]:
                self.swap(currIdx, potentialSwapIdx, self.heap)
                # new curr node = the swapped child index
                currIdx = potentialSwapIdx
                childOneIdx = currIdx * 2 + 1
            # curr node is smaller than both children, nothing left to do
            else:
                break
        
    def siftUp(self, currIdx, heap):
        # Get the parent of the currIdx
        parentIdx = (currIdx - 1) // 2
        # sift up the current index while it is not at the root and
        # it is less than its parent
        while currIdx > 0 and heap[currIdx] < heap[parentIdx]:
            self.swap(currIdx, parentIdx, heap)
            # update the current index to the parent index
            currIdx = parentIdx
            # find the new parent index
            parentIdx = (currIdx - 1) // 2

    def peek(self):
        return self.heap[0]

    def remove(self):
        # Swap root value and last value
        # Pop the new last value
        # siftDown the new root value
        swap(0, len(self.heap - 1), self.heap)
        valToRemove = self.heap.pop()
        self.siftDown(0, len(self.heap) - 1, self.heap)
        return valToRemove
        

    def insert(self, value):
        # Insert the value at the end of the array and siftUp
        self.heap.append(value)
        self.siftUp(len(self.heap) - 1, self.heap)

    def swap(self, i, j, heap):
        heap[i], heap[j] = heap[j], heap[i]
```


