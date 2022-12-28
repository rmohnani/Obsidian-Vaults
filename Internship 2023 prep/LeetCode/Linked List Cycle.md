---
tags:
- leetcode
---
**Title**: 141. Linked List Cycle
**Link**: https://leetcode.com/problems/linked-list-cycle/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 06 : 56

---
# Problem Statement
Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

---
# My Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow = head
        fast = head.next if head else None
        while slow and fast:
            if slow == fast:
                return True

            if slow.next:
                slow = slow.next
            else:
                break
            if fast.next and fast.next.next:
                fast = fast.next.next
            else:
                break
        return False
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        slow, fast = head, head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False

```
notes: more elegant
time complexity: 
space complexity: 

---

