# Chapter: Trees and Graphs
---
# Key Points
- A tree has a root node which has zero ot more child nodes where each child node has zero or more child nodes
- Tree cannot contain cycles
- Binary tree is one in which each node has at most two child nodes
- Node is a 'leaf' if it has no children
- Binary Search tree has the property that for each node n all left descendants are <= n and all right descendants are > n.
- Balanced tree is enough condition to ensure O(log n) time for insert and find.
- Complete binary tree is one in which every level of the tree is fully filled except the last level which is filled left to right
- Full binary tree is one where every node has either 0 or 2 children
- Perfect binary tree is one that is both full and complete. Perfect tree myst have 2^k - 1 nodes where k is number of levels
- **In-Order Traversal**: left -> current -> right. for a bst it visits nodes in ascending order
	```python
	def inorder_traversal(node):
		if (node != None):
			inorder_traversal(node.left)
			visit(node)
			inorder_traversal(node.right)
```
-  **Pre-Order Traversal**: current -> left -> right. Visits current node before it visits children thus "pre". root is always first node visited
	```python
	def preorder_traversal(node):
		if (node != None):
			visit(node)
			preorder_traversal(node.left)
			preorder_traversal(node.right)
```
-  **Post-Order Traversal**: left -> right -> current. Visits current node after it visits children thus "post". root is always last node visited.
	```python
	def postorder_traversal(node):
		if (node != None):
			postorder_traversal(node.left)
			postorder_traversal(node.right)
			visit(node)
```
- A min-heap is a complete binary tree (ie totally filled other than rightmost elements on last level) where each node is smaller than its children, thus the root is the minimmum element in the tree. 
- Max-heap is the same but root is the maximum element in the tree and each node is bigger than its children
- insertion on a min-heap is done at the right most bottom spot (first available spot in tree) to maintain completeness then we swap the element with its parent if it is smaller. This takes O(log n) where n is number of nodes. up-heap ing
- Extracting min is easy since the root is min. To do this we swap the root with the last element (bottom most right most) element then we down-heap it: we chck it against its children and swap it with the smaller of the two children .
- Trie (prefix trees) are a variant of an n-ary tree in which characters are stored at each node and each path down the tree represents a word.
- Trie is commonly used to store the entire english language for quick prefix lookups. Hash table can look up whether string is a valid word it cant check if it is a prefix for valid words, tries can do this quickly in O(k) time where k is length of string.
- A tree is a type of Graph. It is a connected graph without cycles
- Graphs can either be directed or undirected
- If there is path between every pair of vertices the graph is connected.
- Graph can also have cycles
- Graphs can be represented using adjacency lists. Each node would have a list containing each node it has an outgoing edge to. or we could be given a list of tuples [(a,b)] implies a->b.
- Graphs can be represented using adjacency matrices where matrix is NxN where N is number of nodes and a true value at ij implies i->j. For undirected graph adjacency matrix will be symmetric.
- In DFS we start at some node and explore each branch completely before moving to the next. deep before wide
- In BFS we start at some node and explore each neighbor before going to any of their children. wide before deep.
- DFS often preferred if we want to visit every node iin the graph, BFS will also do but DFS is simpler
- To find shortest path between any two nodes BFS is generally better.
- Tree traversals are forms of DFS. When implementing a DFS for a graph we need to check if a node has been visited, because if we don't we could run into an infinite loop.
```python
def search(node: root):
	if (root == None):
		return
	visit(root)
	root.visited = True
	for node in root.adjacent:
		if node.visited == False:
			search(node)
```
- BFS uses a queue
```python
def search(node: root):
	queue = Queue()
	root.marked = true
	queue.enqueue(root)
	while queue not empty:
		node = queue.dequeue()
		visit(node)
		for n in node.adjacent:
			if n.marked == False:
				n.marked = True
				queue.enqueue(n)
```
- Bidirectional search is used to find the shortest path between a source and a destination node. It runs 2 simultaneous breadth-first searches from each node and when they collide returns a path.
---
# Question


# Solution

---
