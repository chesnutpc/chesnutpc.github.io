---
layout: default
title: Run Length Encoding
---

## Run Length Encoding

### Question
Write a function that takes a string and returns its run-length encoding.  Run-length encoding transforms identical consecutive characters into a numerial followed by the character.  For example, "AABBBCCCCD" becomes "2A3B4C1D." To ensure an encoded string can be decoded, runs that exceed 10 characters should be split. For example, "AAAAAAAAAAAAA" (13 A's) should be encoded as "9A4A." 

Sample Input:
string = "ZZXYYYYYYYYYYYYYYY"

Sample Output:
"2Z1X9Y6Y"

### Solution
```
def runLengthEncoding(string):
    # encyrpted string to return, stored as list
    encStr = []
    
    # create list to store last char seen and streak
    # intialize to first char
    data = [string[0], 1]
    # loop through the rest of the string
    for char in string[1:]:
        # if char is the same as stored, increment counter
        if char == data[0]:
            data[1] += 1
            # handle case when counter > 9
            if data[1] > 9:
                encStr.append('9' + data[0])
                # reset counter to 1
                data[1] = 1
        else:
            # if char different, add to encrypted string
            encStr.append(str(data[1]) + data[0])
            # update the data for new char
            data[0] = char
            data[1] = 1
    
    # Append the last bit of data
    encStr.append(str(data[1]) + data[0])
    return ''.join(encStr)
```
O(n) space, 2 times the length of the input string in the worst case\
O(n) time, to iterate through the string



