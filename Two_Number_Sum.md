---
layout: default
title: Two Number Sum
---

## Two Number Sum

### Question
Given an array of unique integers and a target sum, return any two numbers from the input array that sum to the target sum.  If no two numbers sum to the target sum, return an empty array.  The target sum must be obtained by adding two different integers in the array, a single integer cannot be added to itself to obtain the target sum.

Sample Input:
array = [2, 7, 11, 15]\
targetSum = 9

Sample Output: [2, 7]

### Solution #1
```
def twoNumberSum(array, targetSum):
    # Choose first number in the array, then iterate over
    # the remaining numbers, if target sum found stop.
    # If target sum not found, choose 2nd number in the
    # array and iterate over all numbers to the right.
    # Continue until target sum found or if the target
    # sum is not found, return []
    leftIdx = 0
    rightIdx = 1

    while rightIdx < len(array):
        # If the target is found return the numbers
        if array[leftIdx] + array[rightIdx] == targetSum:
            return [array[leftIdx], array[rightIdx]]
        # rightIdx will iterate through remainder of list
        elif rightIdx < len(array) - 1:
            rightIdx += 1
        # If the second index is at the end,
        # shift the first index to the right.
        # Reset the second index to one past the first index
        else:
            leftIdx += 1
            rightIdx = leftIdx + 1
            print(leftIdx)
            print(rightIdx)

    # No match found
    return []

```
O(1) space, only the input array is used\
O(n^2) time, must iterate through the array once for every element



