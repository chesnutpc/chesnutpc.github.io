---
layout: default
title: Permutations
---

## Permutations

### Question
Write a function that takes in an array of unique integers and returns an array of all permutations of those integers in no particular order.

If the input array is empty, the function should return an empty array.

Sample Input:
array = array = [1, 2, 3]

Sample Output:
[[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]

### Solution
```
def getPermutations(array):
    # list that will collect all permutations
    permutations = []
    # call the helper function with the full array, an empty current permutation
    # and the permutations to return
    permutationsHelper(array, [], permutations)
    return permutations

def permutationsHelper(array, currentPermutation, permutations):
    # Base case: no more elements to add we have built at least one element
    if len(array) == 0 and len(currentPermutation) > 0:
        # Append current permutation to permutations
        permutations.append(currentPermutation)
    else:
        # Iterate through each element in the remaining array
        for i in range(len(array)):
            # build new array that excludes the ith element
            newArray = array[:i] + array[i + 1:]
            # Add to the current permutation with the chosen element
            newPermutation = currentPermutation + [array[i]]
            # Recursively call the function with the new permutation
            permutationsHelper(newArray, newPermutation, permutations)
```
O(n x n!) time. There are n! different permutations and you must perform n steps for each\
O(n x n!) space. We must store n! permutations and each one is of length n.
