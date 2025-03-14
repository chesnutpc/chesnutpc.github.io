---
layout: default
title: Suffix Trie Construction
---

## Suffix Trie Construction

### Question
Write a SuffixTrie class for a Suffix-Trie-like data structure.  The class should have a `root` property set to be the root node of the trie and should support:

1. **Creating the trie from a string:** This will be done by calling the `populateSuffixTrie` method upon class instantiation, which should populate the `root` of the class.  
2. **Searching for strings in the trie.**

Note that every string added to the trie should end with the special `endSymbol` character: `'*'`.

Sample Input for Creation:
```
string = "babc"
```

Sample Output for Creation:
```
{
  "c": {"*": true},
  "b": {
    "c": {"*": true},
    "a": {"b": {"c": {"*": true}}}
  },
  "a": {"b": {"c": {"*": true}}}
}
```

Starter Code:
```
class SuffixTrie:
    def __init__(self, string):
        self.root = {}
        self.endSymbol = "*"
        self.populateSuffixTrieFrom(string)

    def populateSuffixTrieFrom(self, string):
        pass

    def contains(self, string):
        pass
```

Sample Input for Searching:
string = "abc"

Sample Output for Searching:
True

### Solution
```
class SuffixTrie:
    def __init__(self, string):
        self.root = {}
        self.endSymbol = "*"
        self.populateSuffixTrieFrom(string)

    def populateSuffixTrieFrom(self, string):
        # As seen in the sample output, the trie will be organized as a 
        # dictionary of dictionaries.  We will iterate through the string, creating
        # a node for each character if not present.  The next character will go into a
        # new dictionary until each reaches the end of a string at which point an 
        # asterisk will be added.
        for i in range(len(string)):
            # helper function to insert substring
            self.insertSubstringStartingAt(i, string)

    def insertSubstringStartingAt(self, i, string):
        # start at the root node
        node = self.root
        # go through all chars in substring
        for j in range(i, len(string)):
            letter = string[j]
            if letter not in node:
                # add the letter as key with an empty value
                node[letter] = {}
            # node should point to the letter
            node = node[letter]
        # entire string has been iterated through, add end symbol
        node[self.endSymbol] = True
    
    def contains(self, string):
        # start at the root node
        node = self.root
        # go through each letter, traversing the trie
        for letter in string:
            if letter not in node:
                return False
            # continue to next node
            node = node[letter]
        # iterated through entire string
        return self.endSymbol in node
```
Complexity for creation:
O(n^2) space in worst case (no repeating suffixes), need to store every possible suffix\
O(n^2) time, nested loops

Complexity for contains:
O(n) time, you must iterate through the string
O(1) space, no storage needed, simply return true or false.
