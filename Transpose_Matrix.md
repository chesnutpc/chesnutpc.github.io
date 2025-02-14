---
layout: default
title: Transpose Matrix
---

## Transpose Matrix

### Question
Write a function that takes in a 2-D array of integers, a.k.a. a matrix, and return the transposition of that matrix.

Sample Input:
```
matrix = [
          [1,2],
          [3,4],
          [5,6]
         ]
```

Sample Output:
```
[
 [1,3,5],
 [2,4,6]
]
```

### Solution
```
def transposeMatrix(matrix):
    # Calc number of rows and columns
    rows = len(matrix)
    cols = len(matrix[0])

    transposedMatrix = []
    
    # Note that to transpose a matrix columns becomes rows.
    # Iterate through each column, creating a new row
    for col in range(cols):
        # Populate new row the elements in the column
        newRow = []
        for row in range(rows):
            newRow.append(matrix[row][col])
        # Append newRow to the transposed matrix
        transposedMatrix.append(newRow)
    return transposedMatrix
```
O(w x h) space, where w is width of the matrix and h is height\
O(w x h) time, to iterate through each element of the matrix



