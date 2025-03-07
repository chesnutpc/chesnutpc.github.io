---
layout: default
title: Bubble Sort Implementation
---

## Bubble Sort Implementation

### Question
Write a function that takes in an array of integers and returns a sorted array using the bubble sort algorithm.
Sample Input:
array = [8,5,2,9,5,6,3]

Sample Output:
[2,3,5,5,6,8,9]

### Hint
Traverse the array swapping any two numbers that are out of order.  Keep track of any swaps that you make.  When you reach the end of the array, if you have made any swaps, repeat.  If no swaps were made, you are done.

### Solution
```
def bubbleSort(array):
    # Bool to monitor if swap occurred
    sorted = False
    while not sorted:
        # Set sorted to true, will change if needed
        sorted = True
        
        # Compare the numbers in the array pairwise
        # Make swaps as needed
        for x in range(len(array) -1):
            if array[x] > array[x+1]:
                array[x], array[x+1] = array[x+1], array[x]
                sorted = False
    return array
```
O(1) space, only the input array is used\
O(n^2) time, contains two nested loops
