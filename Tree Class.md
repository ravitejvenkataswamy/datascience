---
creation date: 2021-06-24 17:48


---
[[2021-06-24]]

### Tree Class
- Another [[Recursive|recursive]] computational [[data structures|data structure]] is the [[tree]]
- We were able to work with trees using [[Data abstraction|data abstraction]] but we can also use Python's object system
- A Tree has a label and a list of branches; each branch is a Tree

Python object system
```python
class Tree:
	def __init__(self, label, branches = []):
		self.label = label
		for branch in branches:
			assert isinstance(branch, Tree)
		self.branches = list(branches)
```
vs. 
using [[Data abstraction]]
```python
def tree(label, branches = []):
	for branch in branches:
		assert is_tree(branch)
	return [label] + list(branches)
def label(tree):
	return tree[0]
def branches(tree):
	return tree[1:]
```

| Python object system                                                                                                                        | Data Abstraction                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| We have to define how to build a tree but don't have to explicitly state how to get to the different attributes out of the constructed tree | We wrote down the constructor and selectors                                                     |
| Here, we wrote down the constructor but the selector are implicit `self.label` will give label and `self.branches` give branches            | More importantly we had to invent a way of combining the pieces like `[label] + list(branches)` |
| When using this method we don't have to think to how combine pieces into a whole                                                            |                                                                                                 |
| Each part is an attribute and an object has all it's attribtes accessed by their name                                                       |                                                                                                 |
|                                                                                                                                             |                                                                                                 |

The definition is little bit easier in the object system but using tree instances is like tree data abstration
###### using Python object system

```python
def fib_tree(n):
	if n == 0 or n== 1:
		return Tree(n)
	else:
		left = fib_tree(n - 2)
		right = fib_tree(n - 1)
		fib_n = left.label + right.label
		return Tree(fib_n, [left, right])
```
Data accessed using dot notation

###### using data abstraction

```python
def fib_tree(n):
	if n == 0 or n == 1:
		return tree(n)
	else:
		left = fib_n(n - 2)
		right = fib_n(n - 1)
		fib_n = label(left) + label(right)
		return tree(fib_n, [left, right])
```
Data accessed using selector function

```ad-summary
The coding style is not any different in Python object system than Data Abstraction method
```

```shell
>>> Tree(1)
Tree(1)
>>> Tree(1, [3, 4])
AssertError
>>> Tree(1, [Tree(3), Tree(4)])
Tree(1, [Tree(3), Tree(4)])
>>> t = Tree(1, [Tree(3), Tree(4)])
>>> print(t)
1
	3 # __repr__ and __str__ and indented are used to achieve this
	4
>>> fib_tree(4)
LARGE OUTPUT, TRY TO PRINT IT ON TERMINAL
```
```ad-note
title: all programs
~~~python
class Tree:
	"""A tree is a label and a list of branches."""
	def __init__(self, label, branches):
		self.label = label
		for branch in branches:
			assert isinstance(branch, Tree)
		self.branches = list(branches)
	def __repr__(self):
		if self.branches:
			branch_str = ', ' + repr(self.branches)
		else:
			branch_str = ''
		return 'Tree({0}{1})'.format(repr(self.label),branch_str)
		
		
	def __str__(self):
		return '\n'.join(self.indented()) #doubt
			
	def indented(self):
		lines = []
		for b in branches:
			for line in b.indented():
				lines.append('	' + line)
		return [str(self.label)] + lines
			
	def is_leaf(self):
		return not self.branches

def fib_tree(n):
	if n == 0 or n== 1:
		return Tree(n)
	else:
		left = fib_tree(n - 2)
		right = fib_tree(n - 1)
		fib_n = left.label + right.label
		return Tree(fib_n, [left, right])
		
def leaves(t):
	"""Return a list of leaf labels in Tree T."""
	if t.is_leaf():
		return [t.label]
	else:
		all_leaves = []
		for b in t.branches:
			all_leaves.extend(leaves(b))
		return all_leaves
	
def height(t):
	""" Returns the number of transitions in the longest path in T. """
	if t.is_leaf():
		return 0
	else:
		return 1 + max([height(b) for b in t.branches])
~~~
```
	
	
	