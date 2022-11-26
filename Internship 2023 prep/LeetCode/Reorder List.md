---
tags:
- leetcode
---
**Title**: 143. Reorder List
**Link**: https://leetcode.com/problems/reorder-list/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln

_Reorder the list to be on the following form:_

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …

You may not modify the values in the list's nodes. Only nodes themselves may be changed.

---
# My Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        second_half_start = head
        second_half_end = head.next
        while second_half_end and second_half_end.next:
            second_half_start = second_half_start.next
            second_half_end = second_half_end.next.next
        
        # reverse second half
        prev, curr = None, second_half_start
        while curr != None:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp
        second_half_start = prev
        
        # interweave lists
        curr = head
        while curr and second_half_start and curr != second_half_start:
            temp1, temp2 = curr.next, second_half_start.next
            curr.next = second_half_start
            second_half_start.next = temp1
            curr, second_half_start = temp1, temp2
        return head
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def reorderList(self, head: ListNode) -> None:
        # find middle
        slow, fast = head, head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

        # reverse second half
        second = slow.next
        prev = slow.next = None
        while second:
            tmp = second.next
            second.next = prev
            prev = second
            second = tmp

        # merge two halfs
        first, second = head, prev
        while second:
            tmp1, tmp2 = first.next, second.next
            first.next = second
            second.next = tmp1
            first, second = tmp1, tmp2
```
notes: 
time complexity: 
space complexity: 

---

