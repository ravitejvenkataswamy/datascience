---
creation date: 2021-06-24 16:14


---
[[2021-06-24]]

### Linked List Mutation
#### Linked Lists can change
- [[attribute assignment|Attribute assignments]] statements can change `first` and `rest` attributes of a `Link`
- The `rest` of a linked list can contain the linked list as a sub-list

```shell
>>> s = Link(1, Link(2, Link(3)))
```
![[Linked List Envir Diagram.excalidraw]]

```shell
>>> s.first = 5
>>> t = s.rest
>>> t.rest = s
>>> s.first
5
>>>> s.rest.rest.rest.rest.rest.first

```
![[Linked Lists can change.excalidraw]]

#### Linked list Mutation Example

##### Adding to an ordered list
![[Linked List example.excalidraw]]
- We have an orderd list, with no repeated and we want to maintain the fact that s is an ordered list with no repeated elements. 
- we need to write a function `add`, that places elemets in the list in the appropriate position so that everything stays in order


```ad-note
If `v` is already in `s`, then don't modify `s`, but still return it.)
```
	
```python
def add(s, v):
	"""Add v to an ordered list s with no repeats, returing modified s."""
	if v < s.first:
		s.rest = s.first
		s.first = v
	return add(s.rest, v)
```

###### Solution
```python
def add(s, v):
	"""Add v to s, returning modified s.
	>>> s = Link(1, Link(3, Link(5)))
	>>> add(s, 0)
	Link(0, Link(1,Link(3, Link(5))))
	>>> add(s, 3)
	Link(0, Link(1,Link(3, Link(5))))
	>>> add(s, 4)
	Link(0, Link(1,Link(3, Link(4, Link(5)))))
	>>> add(s, 6)
	Link(0, Link(1,Link(3, Link(4, Link(5, Link(6))))))
	"""
	assert s in not List.empty
	if s.first > v:
		s.first, s.rest = v, Link(s.first, s.rest) # old s.first and s.rest will used to create a new linked list and will be linked, build a new Link instance
	elif s.first < v and empty(s.rest):
		s.rest = Link(v)
	elif s.first < v:
		add(s.rest, v)
		
	return s	

```
	
![[Pasted image 20210624174020.png]]