---
tags:
- leetcode
---
**Title**: 211. Design Add and Search Words Data Structure
**Link**: https://leetcode.com/problems/design-add-and-search-words-data-structure/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/tries #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 00 : 50 : 16

---
# Problem Statement
Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the `WordDictionary` class:

-   `WordDictionary()` Initializes the object.
-   `void addWord(word)` Adds `word` to the data structure, it can be matched later.
-   `bool search(word)` Returns `true` if there is any string in the data structure that matches `word` or `false` otherwise. `word` may contain dots `'.'` where dots can be matched with any letter.

---
# My Solution
```python
class WordDictionary:

    def __init__(self):
        self.hash = {}
        

    def addWord(self, word: str) -> None:
        curr_hash = self.hash
        for char in word:
            if char not in curr_hash:
                curr_hash[char] = {}
            curr_hash = curr_hash[char]
        curr_hash["None"] = None

    def search_helper(self, s_hash: dict, word: str) -> list:
        next_step = []
        if word == "" and "None" in s_hash:
            return True
        if word == "" and "None" not in s_hash:
            return False
        char = word[0]
        if char != "." and char not in s_hash:
            return False
        if char != "." and char in s_hash:
            return [[s_hash[char], word[1:]]]
        if char == "." and ("None" not in s_hash or len(s_hash) != 1):
            return [[s_hash[n_char], word[1:]] for n_char in s_hash if n_char != "None"]
        else:
            return False


    def search(self, word: str) -> bool:
        search_hashes = [[self.hash,word]]
        while search_hashes:
            for s_hash,phrase in search_hashes:
                search_hashes.pop(0)
                val = self.search_helper(s_hash, phrase)
                # print(val)
                if val is True:
                    return True
                elif val is False:
                    continue
                else:
                    search_hashes.extend(val)
        


# Your WordDictionary object will be instantiated and called as such:
# obj = WordDictionary()
# obj.addWord(word)
# param_2 = obj.search(word)
```
notes: couldn't get it working. got 16/29 tests. Trying to do recursion with hashmaps is very finnicky and I couldn't figure it out.
time complexity: 
space complexity: 

---
# Best Solution
```python
class TrieNode:
    def __init__(self):
        self.children = {}  # a : TrieNode
        self.word = False


class WordDictionary:
    def __init__(self):
        self.root = TrieNode()

    def addWord(self, word: str) -> None:
        cur = self.root
        for c in word:
            if c not in cur.children:
                cur.children[c] = TrieNode()
            cur = cur.children[c]
        cur.word = True

    def search(self, word: str) -> bool:
        def dfs(j, root):
            cur = root

            for i in range(j, len(word)):
                c = word[i]
                if c == ".":
                    for child in cur.children.values():
                        if dfs(i + 1, child):
                            return True
                    return False
                else:
                    if c not in cur.children:
                        return False
                    cur = cur.children[c]
            return cur.word

        return dfs(0, self.root)
```
notes: 
time complexity: 
space complexity: 

---

