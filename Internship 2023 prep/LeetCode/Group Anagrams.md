---
tags:
- leetcode
---
**Title**: 49. Group Anagrams
**Link**: https://leetcode.com/problems/group-anagrams/
**Difficulty**: #leetcode/medium
**Special tags**: #neetcode/arrays_hashing 

---
# Problem Statement

Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

---
# My Solution
```python
class Solution1:
    def getRepresentation(self, phrase: str) -> int:
        val = ['0'] * 26
        
        for char in phrase:
            char_count = val[ord(char) - 97]
            char_count = int(char_count) + 1
            val[ord(char) - 97] = str(char_count)
            
        return "".join(val)
    
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ana_dict = {}
        for phrase in strs:
            phr_key = self.getRepresentation(phrase)
            print(phrase, phr_key)
            if phr_key not in ana_dict:
                ana_dict[phr_key] = [phrase]
            else:
                ana_dict[phr_key].append(phrase)
        
        return ana_dict.values()
```

doesn't work, because can't account for when occurence is more than single digit

```python

```

notes: 
time complexity: 
space complexity: 

---
# Best Solution

notes: 
time complexity: 
space complexity: 

---

