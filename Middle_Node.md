---
layout: default
title: Middle Node
---

## Find the Middle Node from a Singly Linked List

### Question
Given a singly linked list, return the middle node.  If the list has an even number of nodes, return the second of the two middle nodes.  This should be done in O(1) space and O(n) time.

Sample Input:
1 -> 3 -> 2 -> 7 -> 4 -> 5

Sample Output:
7

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


def middleNode(linkedList):
    # The challenge with this question is the time and space complexity
    # requirements.  We will traverse the linked list using two pointers,
    # a slow one and a fast one.  The slow pointer will move to the next
    # node each increment.  While the fast pointer will move two nodes down
    # with each increment.  When the fast pointer reaches the end, the slow
    # pointer should be at the middle node.
    # Initialize the pointers
    slow = linkedList
    fast = linkedList

    # Traverse the list until fast reaches the end
    while fast.next is not None:
        # Try to move the fast pointer two nodes if possible
        if fast.next.next is not None:
            fast = fast.next.next
            slow = slow.next
        # Try to move it one node if it can't be moved two nodes
        elif fast.next is not None:
            fast = fast.next
            slow = slow.next
        # If fast is at the end, exit the loop and return slow
        else:
            break
    return slow
```
O(1) space, no additional data structures needed\
O(n) time, you must traverse the entire linked list
