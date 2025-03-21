---
layout: default
title: Remove Kth Node
---

## Remove the Kth Node from the End of a Singly Linked List

### Question
Given a singly linked list and an integer K, remove the Kth node from the end of the list.  The removal should be done in place and should be done in O(1) space and O(n) time.  If the head of the list is to be removed, it's value and next properties should simply be mutated.

Sample Input:
head = 0 -> 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 // the head node with value 0
k = 4

Sample Output:
0 -> 1 -> 2 -> 3 -> 4 -> 5 -> 7 -> 8 -> 9

Starter Code:
```
class LinkedList:
    def __init__(self, value):
        self.value = value
        self.next = None


def removeKthNodeFromEnd(head, k):
    pass
```

### Solution
```
# This is an input class. Do not edit.
class LinkedList:
    def __init__(self, value):
        self.value = value
        self.next = None


def removeKthNodeFromEnd(head, k):
    # Again the challenge with this problem is the time and space
    # complexity requirements.  We will need to use two pointers,
    # a leading pointer and a lagging pointer.  The leading pointer
    # will seek out the end of the list, and the lagging pointer will
    # remain k + 1 nodes behind.  When the leading pointer reaches the end,
    # the lagging pointer will change the next property to point to the
    # node after the next node.
    # Initialize a counter, leading pointer and lagging pointer
    counter = 1
    lead = head
    lag = head

    # Move the lead pointer k + 1 nodes from the beginning
    while counter <= k:
        lead = lead.next
        counter += 1

    # If the lead pointer is past the last node, then the head of the
    # linked list needs to be "removed."  Remember we just mutate
    # it to keep the head node the same.
    if lead is None:
        head.value = head.next.value
        head.next = head.next.next
        return

    # If you are here, you are not removing the head. Iterate
    # both the lead and lag pointers until lead reaches the
    # end.
    while lead.next is not None:
        lead = lead.next
        lag = lag.next

    # Now the lead pointer is at the end of the list.
    # Simply up update the lag node's next property to 
    # two nodes down
    lag.next = lag.next.next
    return
```
O(1) space, no additional data structures needed\
O(n) time, you must traverse the entire linked list
