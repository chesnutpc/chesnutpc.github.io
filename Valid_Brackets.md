---
layout: default
title: Valid Brackets
---

## Valid Brackets

### Question
Given a string that contains brackets () {} [], write a function that returns true if all brackets are closed properly and false otherwise.

Sample Input:
string = "((){{{{[hello]}}dog}}cat)"

Sample Output:
True

### Solution
```
def balancedBrackets(string):
    # Note that there are opening and closing brackets.
    # Add opening brackets to a stack.
    # When encoutering a closing bracket, check that the bracket
    # on the top of the stack is its corresponding opening bracket.
    # If they match pop the stack, if they don't match return false.
    # If you make it to the end of the string and the stack is empty,
    # return true, otherwise return false.
    stack = []
    for s in string:
        if s in ('(','[','{'): # opening bracket
            stack.append(s)
        elif s in (')',']','}'): # closing bracket
            # check if matching opening bracket is found
            if len(stack) == 0:
                return False
            elif stack[-1] == '(' and s == ')':
                stack.pop()
            elif stack[-1] == '[' and s == ']':
                stack.pop()
            elif stack[-1] == '{' and s == '}':
                stack.pop()
            else:
                return False
        else: # some non-bracket character
            continue
    # must be at the end of the string
    if len(stack) == 0:
        return True
    else:
        return False
```
O(n) space because you need to create a stack \
O(n) time because you must iterate through the stack
