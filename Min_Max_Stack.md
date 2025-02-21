---
layout: default
title: Min Max Stack Construction
---

## Min Max Stack Construction

### Question
Implement a Min Max Stack.  It should support functions to push and pop values from the stack, peek at the top of the stack, return the minimum value and the maximum value in the stack.  All functions should run in constant time and space.  Note: no searching should be necessary to find the minimum and maximum value in the stack.

Starter code:
```
class MinMaxStack:
    def __init(self)__:
        # Write your code here.
        pass

    def peek(self):
        # Write your code here.
        pass

    def pop(self):
        # Write your code here.
        pass

    def push(self, number):
        # Write your code here.
        pass

    def getMin(self):
        # Write your code here.
        pass

    def getMax(self):
        # Write your code here.
        pass
```

### Solution
```
# Feel free to add new properties and methods to the class.
class MinMaxStack:
    def __init__(self):
        # On initialization create two lists
        # One will contain the acutal stack
        self.stack = []
        # The other will contain the minimum and maximum value in the stack
        # This will be a list of tuples (min_val, max_val)
        self.minMaxStack = []
    
    def peek(self):
        # Return the last element of the stack
        return self.stack[len(self.stack) - 1]

    def pop(self):
        # Remove the last element from each stack
        self.minMaxStack.pop()
        return self.stack.pop()

    def push(self, number):
        # Append the number to the end of the list
        self.stack.append(number)
        # Append the (min, max) tuple to the minMaxStack
        # Set currMin, currMax to number to account for first push
        currMin = number
        currMax = number

        # If stack not empty, determine the previous min and max
        if len(self.minMaxStack):
            prevMin = self.minMaxStack[len(self.minMaxStack) -1][0]
            prevMax = self.minMaxStack[len(self.minMaxStack) -1][1]
            # Set the current min and max and append to minMaxStack
            if prevMin <= number:
                currMin = prevMin
            else:
                currMin = number
            if prevMax >= number:
                currMax = prevMax
            else:
                currMax = number
        self.minMaxStack.append((currMin, currMax))
        
    def getMin(self):
        # Return the last tuple in the minMaxStack, position 0
        return self.minMaxStack[len(self.minMaxStack) - 1][0]

    def getMax(self):
        # Return the last tuple in the minMaxStack, position 1
        return self.minMaxStack[len(self.minMaxStack) - 1][1]
```
All functions/methods run in O(1) space and O(1) time.  Nothing is dependent on the length of the stack.


