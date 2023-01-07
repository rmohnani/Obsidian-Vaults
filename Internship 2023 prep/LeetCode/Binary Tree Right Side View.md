---
tags:
- leetcode
---
**Title**: 199. Binary Tree Right Side View
**Link**: https://leetcode.com/problems/binary-tree-right-side-view/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/trees #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 04 : 02

---
# Problem Statement
Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return _the values of the nodes you can see ordered from top to bottom_.

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
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        queue = [root]
        rsv = []
        while queue:
            curr_level = []
            for i in range(len(queue)):
                curr_node = queue.pop(0)
                curr_level.append(curr_node.val)
                if curr_node.left:
                    queue.append(curr_node.left)
                if curr_node.right:
                    queue.append(curr_node.right)
            rsv.append(curr_level[-1])
        return rsv
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rightSideView(self, root: TreeNode) -> List[int]:
        res = []
        q = collections.deque([root])

        while q:
            rightSide = None
            qLen = len(q)

            for i in range(qLen):
                node = q.popleft()
                if node:
                    rightSide = node
                    q.append(node.left)
                    q.append(node.right)
            if rightSide:
                res.append(rightSide.val)
        return 
```
notes: 
time complexity: 
space complexity: 

---

