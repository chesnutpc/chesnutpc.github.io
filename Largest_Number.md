---
layout: default
title: Largest Number
---

## Largest Number

### Question
Write a function that takes a string called `number` and an integer called `numDigits`.  The function should return largest number possible by removing the number of digits specified by `numDigits` from `number`.

Sample Input:
number = "589462"
numDigits = 2

Sample Output:
"8962"

### Solution
```
def bestDigits(number, numDigits):
    # Note that you want the most significant digits to
    # be the largest. Create a stack and iterate through the
    # number adding digits to the stack.  Pop the stack if 
    # current digit is > digit on the top of the stack,
    # and you still have digits that can be removed.
    stack = []
    for digit in number:
        while numDigits > 0 and len(stack) > 0 and digit > stack[-1]:
            stack.pop()
            numDigits -= 1
        stack.append(digit)

    # If you get to the end of number and you still have digits
    # that need to be removed, simply remove the least significant
    # digits.
    while numDigits > 0:
        stack.pop()
        numDigits -= 1

    return ''.join(stack)
```
O(n) space due to the need to create a stack\
O(n) time due to the need to iterate through the number
