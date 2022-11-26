---
tags:
- leetcode
---
**Title**: 19. Remove Nth Node From End of List
**Link**: https://leetcode.com/problems/remove-nth-node-from-end-of-list/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

---
# My Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        last_node = head
        nth_prev_node = dummy
        
        while n > 0:
            last_node = last_node.next
            n -= 1
        
        while last_node:
            last_node = last_node.next
            nth_prev_node = nth_prev_node.next

        nth_prev_node.next = nth_prev_node.next.next
        return dummy.next
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

