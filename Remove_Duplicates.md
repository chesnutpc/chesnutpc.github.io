---
layout: default
title: Remove Duplicates
---

## Remove Duplicates from Singly Linked List

### Question
Given a sorted singly linked list, remove the duplicates.  This should be done without using another data structure like a hash table or set.

Sample Input:
1 -> 1 -> 3 -> 2 -> 4 -> 4 -> 5 -> 5 -> 6 -> 6

Sample Output:
1 -> 3 -> 4 -> 5 -> 6

Starter Code:
```
class LinkedList:
    def __init__(self, value):
        self.value = value
        self.next = None


def removeDuplicatesFromLinkedList(linkedList):
    return None
```

### Solution
```
# This is an input class. Do not edit.
class LinkedList:
    def __init__(self, value):
        self.value = value
        self.next = None


def removeDuplicatesFromLinkedList(linkedList):
    # Since the list is sorted, simple keep track of the value in the
    # previous node and delete the current node if it has the same
    # value.
    # Get the first node of the list
    currNode = linkedList
    # We will traverse the list comparing the current value to the
    # next value
    while currNode.next is not None:
        # In the event they match, set the current node's next property
        # to the following node
        if currNode.value == currNode.next.value:
            currNode.next = currNode.next.next
        # If they don't match, just move on to the next node
        else:
            currNode = currNode.next
    return linkedList
```
O(1) space, no additional data structures needed\
O(n) time, you must traverse the entire linked list
