---
creation date: 2021-06-24 23:28
---
[[2021-06-24]]

### Tree Mutation

#### Example: [[Pruning]] Tree
- Removing subtrees from a tree is called pruning
- Prune branches before recursive processing
- When possible it makes sense to first prune the branches of the current tree, then recursivly prune whichever the branches are left over.
- You can prune a branch before you remove that branch, but since you are removing the whole branch why not remove it first, than prune what's left.
- Problem
	- Lets say we have to prune all of the subtree whose root label is 1
![[IMG_DEE22A286431-1.jpeg]]

```python
def prune(t, n):
	"""Prune all sub-trees whose label is n."""
	t.branches = [b for b in t.branches if b.label != n]
	for b in t.branches:
		prune(b,n)
```