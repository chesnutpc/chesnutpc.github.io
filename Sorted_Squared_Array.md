---
layout: default
title: Sorted Squared Array
---

## Sorted Squared Array

### Question
Write a function that takes an array of integers in ascending order and returns an array of the squared integers in ascending order.  Be sure to account for negative numbers.  Try to do this without sorting.

Sample Input:
array = [-4,-1,0,3,10]

Sample Output:
[0,1,9,16,100]

### Solution
```
def sortedSquaredArray(array):
    # Create an array with place holder numbers
    output = [0] * len(array)
    # We will create a left pointer and right pointer and
    # set them to the first and last elements, respectively.
    # We also need an output pointer to keep track of where to
    # place the squared value.
    leftPtr = 0
    rightPtr = len(array) - 1
    outPtr = len(array) - 1
    # We will work our way in comparing the values pointed to
    # by the left and right pointers.  Choose the value with the
    # biggest absolute value, square it and add it to the output
    # array adjusting the pointers as needed.
    while leftPtr <= rightPtr:
        if abs(array[leftPtr]) >= abs(array[rightPtr]):
            output[outPtr] = array[leftPtr] * array[leftPtr]
            leftPtr += 1
            outPtr -= 1
        else: # abs(array[leftPtr]) < abs(array[rightPtr])
            output[outPtr] = array[rightPtr] * array[rightPtr]
            rightPtr -= 1
            outPtr -= 1
    return output
```
O(n) space, only used array of same length as inputted array\
O(n) time, inputted array is iterated through once


