---
tags:
- leetcode
---
**Title**: 102. Binary Tree Level Order Traversal
**Link**: https://leetcode.com/problems/binary-tree-level-order-traversal/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/trees #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 20 : 27

---
# Problem Statement
Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).

---
# My Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        queue = [root]
        level_order = []
        while queue:
            curr_level = []
            for i in range(len(queue)):
                node = queue.pop(0)
                curr_level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            level_order.append(curr_level)
        return level_order
```
notes: should not have taken 20 mins, didn't realize my failure case was when root is None, so just added an if at the top to catch that.
time complexity: 
space complexity: 

---
# Best Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None


class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        res = []
        q = collections.deque()
        if root:
            q.append(root)

        while q:
            val = []

            for i in range(len(q)):
                node = q.popleft()
                val.append(node.val)
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            res.append(val)
        return res
```
notes: 
time complexity: 
space complexity: 

---

