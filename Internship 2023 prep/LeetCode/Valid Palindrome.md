---
tags:
- leetcode
---
**Title**: 125. Valid Palindrome
**Link**: https://leetcode.com/problems/valid-palindrome/
**Difficulty**: #leetcode/difficulty/easy  
**Special tags**: #neetcode/area/two_pointers 
**Status**: #leetcode/status/completed   

---
# Problem Statement

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.

---
# My Solution
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        clean_s = ""
        # cleans string to remove non alphanumeric characters
        for char in s:
            if char.isalnum():
                clean_s += char.lower()
	    
        pointer_1 = 0
        pointer_2 = len(clean_s) - 1
        while pointer_1 < pointer_2:
            if clean_s[pointer_1] != clean_s[pointer_2]:
                return False
            pointer_1 += 1
            pointer_2 -= 1
        
        return True
```
notes: Cleans string to remove non alphanumeric characters. Then uses two pointers, one starting at the beginning and one at the end and checks if characters at those positions are equal, then moves them to the next and previous char respectively until the pointers cross. If dont match not palindrome else it is.
time complexity: O(n)
space complexity: O(n) for the clean string

---
# Best Solution
#leetcode/got_best_solution 
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) - 1
        while l < r:
            while l < r and not self.alphanum(s[l]):
                l += 1
            while l < r and not self.alphanum(s[r]):
                r -= 1
            if s[l].lower() != s[r].lower():
                return False
            l += 1
            r -= 1
        return True

    # Could write own alpha-numeric function
    def alphanum(self, c):
        return (
            ord("A") <= ord(c) <= ord("Z")
            or ord("a") <= ord(c) <= ord("z")
            or ord("0") <= ord(c) <= ord("9")
        )
```
notes: Better because it doesnt use extra space and doesnt use pythons isalnum function. It just keeps moving left and right respectively until it encounters the next valid character which is smarter.
time complexity: O(n)
space complexity: O(1)

---

