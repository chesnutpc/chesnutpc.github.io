---
layout: default
title: Product Sum
---

## Product Sum

### Question
Write a function that takes in a "special" array and returns its product sum.

A "special" array is a non-empty array that contains either integers or other "special" arrays. The product sum of a "special" array is the sum of its elements, where "special" arrays inside it are summed themselves and then multiplied by their level of depth.

The depth of a "special" array is how far nested it is. For instance, the depth of [] is 1; the depth of the inner array in [[]] is 2; the depth of the innermost array in [[[]]] is 3.

Therefore, the product sum of [x, y] is x + y; the product sum of [x, [y, z]] is x + 2 * (y + z); the product sum of [x, [y, [z]]] is x + 2 * (y + 3 * z).

Sample Input:
array = [5, 2, [7, -1], 3, [6, [-13, 8], 4]]

Sample Output:
12  // calculated as: 5 + 2 + 2 * (7 - 1) + 3 + 2 * (6 + 3 * (-13 + 8) + 4)

### Solution
```
def productSum(array, multiplier = 1):
    # We will iterate through each element in the array keeping a running
    # total of the sum.  
    sum = 0
    for element in array:
        if type(element) is list:
            # If the element is an array, recursively call productSum
            # adding 1 to the mulitplier
            sum += productSum(element, multiplier + 1)
        else:
            # If the element in an integer, add to the sum
            sum += element
    # When finished iterating through the array or sub-array, 
    # return sum x multiplier
    return sum * multiplier
```
O(d) space where d is the depth of the tree, recursive call add to the stack\
O(n) time where n is the number of elements in tht array, must iterate through each
