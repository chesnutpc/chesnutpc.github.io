---
layout: default
title: Palindrome
---

## Palindrome Check

### Question
Write a function that takes string and returns a boolean indicating if the string is a palidrome

Sample Input:
`str = 'level'`

Sample Output:
`True`

### Naive Solution
```
def isPalindrom(string):
  # Create a new string that reverses the input string
  # string[::-1] slice the string end to beginning
  # string[start:end:step]
  reverseString = string[::-1]
  # compare the input and reverse string
  return string == reverseString
```
O(n) space because we create a new string from the input string.\
O(n) time because the reversed string is created in O(n) time using slices and string comparison is also O(n) in Python.\
O(n) [reversal] + O(n) [comparison] = O(2n) = O(n)
If you were create the reverse string by looping through each letter, the time would be O(n^2) because you are concatenating each new letter to the end of a string.
