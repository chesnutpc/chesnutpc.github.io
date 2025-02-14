---
layout: default
title: Validate Subsequence
---

## Validate Subsequence

### Question
Write a function that takes two arrays of integers and returns a bool indicating if the second array is a subsequence of the first.  Note that the numbers of the subsequence must appear in the same order as in the array, but they need not be consecutive in the array.

Sample Input:
array = [3, 6, 23, 7, 2, 4]
sequence = [3, 7, 4]

Sample Output:
True

### Solution
```
def isValidSubsequence(array, sequence):
    # Create two pointers for array and sequence
    arrPtr = 0
    seqPtr = 0
    # Loop through both arrays checking if the numbers match
    # If they match, increment the sequence pointer
    # If the sequence pointer reaches the length of the array,
    # return true.
    while arrPtr < len(array):
        if array[arrPtr] == sequence[seqPtr]:
            seqPtr += 1
            if seqPtr == len(sequence):
                return True
        arrPtr += 1

    # Not a subsequence
    return False
```
O(1) space, only the input arrays are used\
O(n) time, where n is the length of the array, must iterate over the entire array



