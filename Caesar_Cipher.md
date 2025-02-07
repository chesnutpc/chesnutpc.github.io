---
layout: default
title: Caesar Cipher Encryptor
---

## Caesar Cipher Encryptor

### Question
Given a string of lower case letters and a positive interger k , return a string of letters that are shifted by k positions in the alphabet.  Note that the letters should wrap around the alphabet.

Sample Input:
string = "xyz"
key = 2

Sample Output:
"zab"

### Solution
```
def caesarCipherEncryptor(string, key):
    # Note that strings are immutable in Python
    # You cannot use a pointer approach to change a single char in a string.
    # My answer converts the string to a list of letters, performs
    # the encryption and then returns the list converted back to a string.
    
    # Convert the string to a list
    chars = list(string)
    # Loop through each char, apply Caesar Cipher
    for i in range(len(chars)):
        # Convert each letter to its ascii number
        # Note ascii letter a = 97, z = 122
        # Subtract 97 so that a = 0 and z = 25
        char_num = ord(chars[i]) - 97
        # Perform the shift use mod operator to wrap around the alphabet
        enc_num = (char_num + key) % 26
        # Convert the encrypted ascii number back to character and modify string
        chars[i] = chr(enc_num + 97)
    return ''.join(chars)
```
O(n) space due to the need to create a list\
O(n) [convert string to list] + O(n) [convert list to string] = O(2n) = O(n)

Pitfall: Mapping a to 1 instead of 0.  This will cause the modulo operation to not perform as expected.

