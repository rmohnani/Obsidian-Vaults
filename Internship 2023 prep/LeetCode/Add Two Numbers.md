---
tags:
- leetcode
---
**Title**: 2. Add Two Numbers
**Link**: https://leetcode.com/problems/add-two-numbers/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed 
**Time**:   00 : 20 : 06

---
# Problem Statement
You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

---
# My Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        ans = ListNode()
        dummy = ans
        curr1 = l1
        curr2 = l2
        carry = 0
        while curr1 and curr2:
            dummy.next = ListNode()
            dummy = dummy.next

            added = curr1.val + curr2.val + carry
            if added >= 10:
                rem = added - 10 
                carry = 1
            else:
                rem = added
                carry = 0
            
            dummy.val = rem
            curr1 = curr1.next
            curr2 = curr2.next
        
        while curr1:
            dummy.next = ListNode()
            dummy = dummy.next
            rem = curr1.val + carry
            if rem >= 10:
                rem -= 10
                carry = 1
            else:
                carry = 0
            dummy.val = rem
            curr1 = curr1.next
        
        while curr2:
            dummy.next = ListNode()
            dummy = dummy.next
            rem = curr2.val + carry
            if rem >= 10:
                rem -= 10
                carry = 1
            else:
                carry = 0
            dummy.val = rem
            curr2 = curr2.next
        
        if carry != 0:
            dummy.next = ListNode(carry)
            
        
        return ans.next
```
notes: Not as elegant as possible I think
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
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode()
        cur = dummy

        carry = 0
        while l1 or l2 or carry:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0

            # new digit
            val = v1 + v2 + carry
            carry = val // 10
            val = val % 10
            cur.next = ListNode(val)

            # update ptrs
            cur = cur.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None

        return dummy.next

```
notes: More elegant
time complexity: 
space complexity: 

---

