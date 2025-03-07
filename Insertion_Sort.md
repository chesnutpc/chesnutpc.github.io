---
layout: default
title: Insertion Sort Implementation
---

## Insertion Sort Implementation

### Question
Write a function that takes in an array of integers and returns a sorted array using the insertion sort algorithm.
Sample Input:
array = [8,5,2,9,5,6,3]

Sample Output:
[2,3,5,5,6,8,9]

### Hint
Divide the array in place between a sorted portion and an unsorted portion. Take each number from the unsorted portion and insert it in to the correct position in the sorted portion by make swaps as needed.


### Solution
```
def insertionSort(array):
    # The first element of the list is sorted by definition
    # The outer loop will start with the second element
    # Will keep track of the first element of the unsorted portion
    for i in range(1, len(array)):
        # Set j to i, this will move to left as we move numbers from
        # the unsorted portion to the sorted portion
        j = i

        # While j is not at the beginning of the list and the current element
        # is smaller than its predecessor, swap the two elements
        while j > 0 and array[j] < array[j - 1]:
            swap(j, j - 1, array)
            j -= 1

    return array

def swap(i, j, array):
    array[i], array[j] = array[j], array[i]
```
O(1) space, only the input array is used\
O(n^2) time, contains two nested loops
