---
tags:
- leetcode
---
**Title**: 49. Group Anagrams
**Link**: https://leetcode.com/problems/group-anagrams/
**Difficulty**: #leetcode/difficulty/medium
**Special tags**: #neetcode/area/arrays_hashing 
**Status**: #leetcode/status/completed 

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
class Solution2:
    def getRepresentation(self, phrase: str) -> int:
        str_dict = {}
        for char in phrase:
            str_dict[char] = 1 + str_dict.get(char, 0)
        str_repr = ""
        for key in sorted(str_dict.keys()):
            str_repr += key + str(str_dict[key])
        return str_repr
    
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ana_dict = {}
        for phrase in strs:
            phr_dict_str = self.getRepresentation(phrase)
            if phr_dict_str not in ana_dict:
                ana_dict[phr_dict_str] = [phrase]
            else:
                ana_dict[phr_dict_str].append(phrase)
        return ana_dict.values()
```

notes: Everything else was correct, just needed a better representation for the string that can be easily compared against everything and is a string.

time complexity: 
space complexity: 

---
# Best Solution

```python
class Solution:
	def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
		ans = collections.defaultdict(list)
		for s in strs:
			count = [0] * 26
			for c in s:
				count[ord(c) - ord('a')] += 1
			ans[tuple(count)].append(s)
		
		return ans.values()
```

notes: Smart! Since lists and dictionaries can't be used as dictionary keys it creates a list representing the counts which is what I was doing but better because it doesn't try to make it a pseudo-bit string so it doesn't have the issue of double digit counts. It then turns this list into a tuple to use it as a key and stores the particular string in a list as the value

time complexity: O(C), C = total characters across all strings in list
space complexity: O(n), n = no. of strings in list

---

