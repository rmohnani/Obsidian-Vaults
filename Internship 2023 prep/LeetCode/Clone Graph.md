---
tags:
- leetcode
---
**Title**: 133. Clone Graph
**Link**: https://leetcode.com/problems/clone-graph/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/graphs #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 26 : 17

---
# Problem Statement
Given a reference of a node in a **[connected](https://en.wikipedia.org/wiki/Connectivity_(graph_theory)#Connected_graph)** undirected graph.

Return a [**deep copy**](https://en.wikipedia.org/wiki/Object_copying#Deep_copy) (clone) of the graph.

Each node in the graph contains a value (`int`) and a list (`List[Node]`) of its neighbors.
```
class Node {
    public int val;
    public List<Node> neighbors;
}
```

---
# My Solution
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        if not node:
            return None
        new_nodes = {}
        visited = set()
        queue = collections.deque()
        queue.append(node)


        while queue:
            # print(queue)
            curr_o_node = queue.popleft()
            if curr_o_node.val not in new_nodes:
                new_nodes[curr_o_node.val] = Node(curr_o_node.val)
            if curr_o_node not in visited:
                visited.add(curr_o_node)
                curr_n_node = new_nodes[curr_o_node.val]
                for neighbor in curr_o_node.neighbors:
                    if neighbor.val not in new_nodes:
                        new_nodes[neighbor.val] = Node(neighbor.val)
                    curr_n_neighbor = new_nodes[neighbor.val]
                    curr_n_node.neighbors.append(curr_n_neighbor)
                    queue.append(neighbor)
        return new_nodes[1]

```
notes: It actually worked I was just missing the case where node is none.
time complexity: 
space complexity: 

---
# Best Solution
```python


class Solution:
    def cloneGraph(self, node: "Node") -> "Node":
        oldToNew = {}

        def dfs(node):
            if node in oldToNew:
                return oldToNew[node]

            copy = Node(node.val)
            oldToNew[node] = copy
            for nei in node.neighbors:
                copy.neighbors.append(dfs(nei))
            return copy

        return dfs(node) if node else None
```
notes: simpler solution using dfs.
time complexity: 
space complexity: 

---

