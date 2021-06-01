---
date updated: '2021-05-29T16:27:40+05:30'

---

Generators

- Is a special kind of [[iterator]] just like a [[map]] is a special kind of [[iterator]]
- Returned form a [[generator function]]
  - Used the keyword [[yield]] instead of return
```python

def plus_minus(x):
yield x
yield -x
```

- ```>>> t = plus_minus(3)

> > > next(3)

3

> > > next(3)

-3

> > > t

<generator object plus_minus ...>```
- A generator function is a function that [[yield]]s values instead of returning them
        - A normal function returns once; a generator function can [[yield]] multiple times
        - generator is an iterator created automatically by calling a generator function
        - When a generator function is called, it returns a generator that iterates over its yields
```python
def evens(start, end):
	even = start + (start % 2)
    while even < end:
      yield even
      even += 2
```

- `evens`is a generator function
```
>>> list(evens(1,10))
[2,4,6,8]

> > > t = evens(2, 10)
```
==Not even begun executing the body of this function yet, it's not until next is called that the body begin the execute==
```
>>> next(t)
2
```

==Keeps executing until the yield statement is reached, as the next element 2 is yield in the iterator t==
**Execution paused here and still remember all of the environment of the function execution so that when the next is called it will continue form incrementing even by 2**
```>>> next(t)
4

> > > 
```

- [[Lazy computing]] will be used

[[generators]] and [[iterator]]
  - [[generator function]] return [[generators]] but they often process [[iterator]]s in the course of their execution
  - [[yield from]]
    - A yield from statement yields all values from an [[iterator]] or [[iterable]] (python 3.3 onwards)))
```>>> list(a_then_b([3,4],[5,6]))

[3,4,5,6]
```

```python
def a_then_b(a, b):
  for x in a:
    yield x
  for x in b:
    yield x
```


==simpler way== both are completely equivalent
```python
def a_then_b(a, b):
	yield form a
    yield form b
```

```list(countdown(5))
[5,4,3,2,1]
```

```python
def countdown(k):
  if k > 0:
    yield k
    yield from countdown(k - 1)
  else:
    yield 'blast off'
```

```
 >>> for k in countdown(3):
...     print(k)
...
3
2
1
blast off
```

```python

def prefixes(s):
	if s: #Non empty, very clever
		yielf from prefixes(s[:-1])
		yield s
	def substrings(s):
		if s:
		yield from prefixes(s)
		yield from substrings(s[1:])
```
