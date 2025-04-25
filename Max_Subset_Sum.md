---
layout: default
title: Max Subset Sum
---

## Max Subset Sum

### Question
Write a function that takes in an array of positive integers and returns the maximum sum of non-adjacent elements in the array.

If the input array is empty, the function should return 0.

Sample Input:
array = [75, 105, 120, 75, 90, 135]

Sample Output:
330  // 75 + 120 + 135

### Solution
```
def maxSubsetSumNoAdjacent(array):
    # Create a new array (maxSums) of the same length of the
    # inputted array.  At each index, store the maximum
    # sum that can be generated using no adjacent numbers
    # located between the index 0 and the current index.

    #             max of:
    # maxSum[i] = 1) maxSum[i-1]
    #             2) maxSum[i-2] + array[i]

    # Check if array is empty
    if len(array) == 0:
        return 0

    # If array is length 1, return the value
    if len(array) == 1:
        return array[0]

    # copy array to maxSums
    maxSums = array[:]
    # Note that maxSums[0] = array[0], nothing more to do
    # maxSums[1] should be the max of array[0] and array[1]
    maxSums[1] = max(array[0], array[1])

    # Now we can start applying the formula above
    for i in range(2, len(array)):
        maxSums[i] = max(maxSums[i-1], maxSums[i-2] + array[i])

    # Return the last element of maxSums
    return maxSums[-1]
```
O(n) time as we must iterate through the array once\
O(n) space as we create a new array that is the same length as the inputted array\
