---
layout: default
title: Number of Ways to Traverse Grid
---

## Number of Ways to Traverse Grid

### Question
You’re given two positive integers representing the width and height of a grid-shaped, rectangular graph. Write a function that returns the number of ways to reach the bottom right corner of the graph when starting at the top left corner. Each move you take must either go down or right. In other words, you can never move up or left in the graph.

For example, given the graph illustrated below, with width = 2 and height = 3, there are three ways to reach the bottom right corner when starting at the top left corner:

```
 _ _
|_|_|
|_|_|
|_|_|
```
1. Down, Down, Right  
2. Right, Down, Down  
3. Down, Right, Down

Sample Input:
```
width = 4
hieght = 3
```

Sample Output:
```
10
```

### Solution
```
def numberOfWaysToTraverseGraph(width, height):
    # We will create a new array of the same width and
    # height of the inputted array.  Each element will
    # indicate the number of ways to reach the square.
    # The upper left corner has only 1 way to reach the
    # square.  Likewise, there is only 1 way to reach 
    # each square on the top or left edge of the grid.
    # All the other squares are the sum of the square
    # to the top and left, since you may only traverse
    # down and to the right.

    # Create an empty array of zeros of the same width
    # and height of the inputted array.
    numOfWays = [[0 for _ in range (width + 1)] for _ in range(height + 1)]

    # Now we just implement the logic above summing
    # squares when neeeded.
    for widthIdx in range(1, width + 1):
        for heightIdx in range(1, height + 1):
            # Set left edge and top edge to 1
            if widthIdx == 1 or heightIdx == 1:
                numOfWays[heightIdx][widthIdx] = 1
            # For other boxes sum box to left and box above
            else:
                left = numOfWays[heightIdx][widthIdx - 1]
                up = numOfWays[heightIdx - 1][widthIdx]
                numOfWays[heightIdx][widthIdx] = left + up
    # When finished return the value in the lower right
    return numOfWays[height][width]
    
```
O(n x m) time as we must iterate through the array once\
O(n x m) space as we create a new array that is the same size as the inputted array\
