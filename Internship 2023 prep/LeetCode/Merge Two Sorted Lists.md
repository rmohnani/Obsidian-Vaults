---
tags:
- leetcode
---
**Title**: 21. Merge Two Sorted Lists
**Link**: https://leetcode.com/problems/merge-two-sorted-lists/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  

---
# Problem Statement
You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list_.

---
# My Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        merged_list = ListNode()
        dummy_head = merged_list
        while list1 != None and list2 != None:
            if list1.val <= list2.val:
                merged_list.next = list1
                list1 = list1.next
            else:
                merged_list.next = list2
                list2 = list2.next
            merged_list = merged_list.next
        
        if list1 != None:
            merged_list.next = list1
        
        if list2 != None:
            merged_list.next = list2
        
        return dummy_head.next
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: ListNode, list2: ListNode) -> ListNode:
        dummy = ListNode()
        tail = dummy

        while list1 and list2:
            if list1.val < list2.val:
                tail.next = list1
                list1 = list1.next
            else:
                tail.next = list2
                list2 = list2.next
            tail = tail.next

        if list1:
            tail.next = list1
        elif list2:
            tail.next = list2

        return dummy.next
```
notes: slightly cleaner
time complexity: 
space complexity: 

---

