---
creation date: 2021-06-24 10:59
---
[[2021-06-24]]

### Linked List Processing
- As we can't use built - in functions like range, map and filter we need to create our own user defined funtions like range_link, map_link and filter_link , like shown below:

```python
square, odd = lambda x: x * x, lambda x: x % 2 == 1
list(map(square, filter(odd, range(1, 6)))) # [1, 9 ,25]
map_link(square, filter_link(odd, range_link(1, 6))) # Link(1, Link(9, Link(25)))
```

- Let's implement `range_link` , `map_link` and  `filter_link`
```python
def range_link(start, end):
	""" Return a Link(class) containing consecutive integers from start to end.
	>>> range_link(3, 6)
	Link(3, Link(4, Link(5)))
	"""
	if start >= end:
		return Link.empty
	else:
		return Link(start, range_link(start+1, end))
	
```

```python
def map_link(f, s):
	"""Return a Link that contains f(x) for each x in Link s.
	>>> map_link(square, range_link(3, 6))
	Link(9, Link(16, Link(25)))
	"""
	
	if s is Link.empty:
		return s
	else:
		return Link(f(s.first), map_link(f,s.rest))
```
#revise
here `f` is equivalent to `odd` or any other function
saying `f(s.first) == odd(s.first)`
Keep in mind
```python
def filter_link(f, s):
	"""Return a Link that contains only the elements x of Link s for which f(x) is a true value.
	>>> filter_link(odd, range_link(3, 6))
	Link(3, Link(5))
	"""
	
	if s is Link.empty:
		return s
	filtered_rest = filter_link(f, s.rest)
	if f(s.first):
		return Link(s.first, filtered_rest)
	else:
		return filtered_rest
```

```ad-note
title: Required class and functions
~~~python
class Link:
	empty = ()
	def __init__(self, first, rest = empty):
		assert rest is Link.empty or isinstance(rest, Link)
		self.first = first
		self.rest = rest
		
	def __repr__(self):
		if self.rest:
			rest_repr = ', ' + repr(self.rest)
		else:
			rest_repr = ''
			return 'Link(' + repr(self.first) + rest_repr + ')'
	def __str__(self):
		string = '<'
		while self.rest is not Link.empty:
			string += str(self.first) + ' '
			self = self.rest
		return string + str(self.first) + '>'
		
def square(x):
	return x * x
	
def odd(c):
	return c % 2 == 1

~~~	
```

```shell
>>> r = range_link(1, 6)
>>> s = filter_link(odd, r)
>>> t = map_link(square, s)
>>> t
Link(1, Link(9, Link(25)))
>>> print(t)
<1 9 25>
```