---
tags:
- leetcode
---
**Title**: 206. Reverse Linked List
**Link**: https://leetcode.com/problems/reverse-linked-list/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  

---
# Problem Statement
Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.

---
# My Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev, curr = None, head

        while curr != None:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp
        return prev
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

