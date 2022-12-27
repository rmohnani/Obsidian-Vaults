---
tags:
- leetcode
---
**Title**: 138. Copy List with Random Pointer
**Link**: https://leetcode.com/problems/copy-list-with-random-pointer/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/linked_list #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
A linked list of length `n` is given such that each node contains an additional random pointer, which could point to any node in the list, or `null`.

Construct a [**deep copy**](https://en.wikipedia.org/wiki/Object_copying#Deep_copy) of the list. The deep copy should consist of exactly `n` **brand new** nodes, where each new node has its value set to the value of its corresponding original node. Both the `next` and `random` pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. **None of the pointers in the new list should point to nodes in the original list**.

For example, if there are two nodes `X` and `Y` in the original list, where `X.random --> Y`, then for the corresponding two nodes `x` and `y` in the copied list, `x.random --> y`.

Return _the head of the copied linked list_.

The linked list is represented in the input/output as a list of `n` nodes. Each node is represented as a pair of `[val, random_index]` where:

-   `val`: an integer representing `Node.val`
-   `random_index`: the index of the node (range from `0` to `n-1`) that the `random` pointer points to, or `null` if it does not point to any node.

Your code will **only** be given the `head` of the original linked list.

---
# My Solution
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x: int, next: 'Node' = None, random: 'Node' = None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution:
    def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        old_to_new = {None: None}

		# first pass to create new equivalents for each node
        curr = head
        while curr != None:
            new_node = Node(curr.val)
            old_to_new[curr] = new_node
            curr = curr.next
        # second pass to make next and random connections between new nodes using old
        curr = head
        while curr != None:
            new_node = old_to_new[curr]
            new_node.next = old_to_new[curr.next]
            new_node.random = old_to_new[curr.random]
            curr = curr.next
        return old_to_new[head]
```
notes: Since deep copying, need first pass
time complexity: O(n)
space complexity: O(n), n for hashmap and n in new linkedlist

---
# Best Solution

notes: same as mine
time complexity: 
space complexity: 

---

