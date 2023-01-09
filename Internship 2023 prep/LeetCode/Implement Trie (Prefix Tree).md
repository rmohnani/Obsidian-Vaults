---
tags:
- leetcode
---
**Title**: 208. Implement Trie (Prefix Tree)
**Link**: https://leetcode.com/problems/implement-trie-prefix-tree/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/tries #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 10 : 29

---
# Problem Statement
A [**trie**](https://en.wikipedia.org/wiki/Trie) (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

-   `Trie()` Initializes the trie object.
-   `void insert(String word)` Inserts the string `word` into the trie.
-   `boolean search(String word)` Returns `true` if the string `word` is in the trie (i.e., was inserted before), and `false` otherwise.
-   `boolean startsWith(String prefix)` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.

---
# My Solution
```python
class Trie:

    def __init__(self):
        self.hash = {}
        

    def insert(self, word: str) -> None:
        curr_hash = self.hash
        for char in word:
            if char not in curr_hash:
                curr_hash[char] = {}
            curr_hash = curr_hash[char]
        
        curr_hash[None] = None

        

    def search(self, word: str) -> bool:
        curr_hash = self.hash
        for char in word:
            if char not in curr_hash:
                return False
            curr_hash = curr_hash[char]
        if None in curr_hash:
            return True
        else:
            return False

    def startsWith(self, prefix: str) -> bool:
        curr_hash = self.hash
        for char in prefix:
            if char not in curr_hash:
                return False
            curr_hash = curr_hash[char]
        return True
        


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class TrieNode:
    def __init__(self):
        self.children = [None] * 26
        self.end = False


class Trie:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.root = TrieNode()

    def insert(self, word: str) -> None:
        """
        Inserts a word into the trie.
        """
        curr = self.root
        for c in word:
            i = ord(c) - ord("a")
            if curr.children[i] == None:
                curr.children[i] = TrieNode()
            curr = curr.children[i]
        curr.end = True

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the trie.
        """
        curr = self.root
        for c in word:
            i = ord(c) - ord("a")
            if curr.children[i] == None:
                return False
            curr = curr.children[i]
        return curr.end

    def startsWith(self, prefix: str) -> bool:
        """
        Returns if there is any word in the trie that starts with the given prefix.
        """
        curr = self.root
        for c in prefix:
            i = ord(c) - ord("a")
            if curr.children[i] == None:
                return False
            curr = curr.children[i]
        return True
```
notes: Uses node object instead of a dictionary, limits it to characters only, using hashmap allows more special characters and is more generalizable
time complexity: 
space complexity: 

---

