- A linked list is either empty or a first value and the rest of the  value in a linked list.
![[Linked List Structure.excalidraw]]

- We don't just write 3, 4, 5 that will be a tuple

- We have to write the constructor

- convention are used, as there are more popular in computer science
### Construction the Linked list

```python
class List:
	
	empty  = () #Some zero - length sequence

	def __init__(self, first, rest = empty):
		assert rest is Link.empty or isinstance(rest, Link)
		self.first = first
		self.last = last
```

- here [[isinstance]] is used to check if rest is an instance of the `Link` class meaning it itslef is a linked list
```shell
>>> - Link(3, Link(4, Link(5)))
Link(3, Link(4, Link(5)))
>>> s = Link(3, Link(4, Link(5)))
>>> s.first
3
>>> s.rest.first
4
>>> s.rest.rest.first
5
>>> s.rest.rest.rest is Link.empty
True
>>> s.rest.first = 7 #can be modified
>>> s
Link(3, Link(4, Link(5)))
>>>
```
- The listed lists are designed to be immutalbe
```shell
>>> Link(8, s.rest)
Link(8, Link(7, Link(5)))
>>> s
Link(3, Link(7, Link(5)))
>>>
```

- Here the origianal list is unmodified