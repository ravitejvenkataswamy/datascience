---
date updated: '2021-05-31T19:14:04+05:30'

---

# Iterators

#done

#### Introduction

- A [[container]] can provide an iterator that provides access to its elements in some order
- Here are [[built-in functions]]
- [[Iter]][[iterable]]: Returns an iterator over the elements of an iterable value
- [[next]][[iterable]]: Return the next element in an iterator

```python
>>> s = [3, 4, 5]
>>> t = iter(s)
>>> next(t)
3
>>> next(t)
4
>>> u = iter(s)
>>> next(u)
3
```

- Here both t and u are iterating over same values but otherwise they're independent
- Slightly complicated list, [[Nested list]]
-

```python
>>> s =[[1,2],3,4,5]
>>> t = iter(s)
>>> next(s)
Type Error: 'List' object is not an iterator
>>> t = iter(s)
>>> next(t)
[1,2] #gives the index 0
```

#### [[Dictionary]] iteration

- Views of contents of Dictionary
- An [[iterable]] value is any that can be passed to [[Iter]] to produce an [[iterator]]
- An [[iterator]] is returned from [[iter]] and can be passed to [[next]]; all [[iterator]]s are [[mutable]]
- ==All [[iterator]]s are [[mutable]] when you call [[next]] on them they mutate and point to next element==
- A [[Dictionary]], its keys, its values, and its items are all [[iterable]] values
- **The order of items in a dictionary is the order in which they were added (Python 3.6 above)**
- Historically, items appeared in an arbitrary order before Python 3.5 and earlier
- ==Ordering Dictionaries is not reliable==

```python
>>> d = {'one':1, 'two': 2, 'three':3}
>>> d['zero'] = 0
>>> k = iter(d.key()) # or iter(d)
>>>next(k)
'one'
>>> next(k)
'two'
>>> next(k)
'three'
>>> next(k)
'zero'
>>> v = iter(d.values()) #will return the values in order of which the dictionary was created
>>> next(v)
1
>>> next(v)
2
>>> next(v)
3
>>> next(v)
0

>>> i = iter(d.items())
>>> next(i)
('one',1)
>>> next(i)
('two',2)
>>> next(i)
('three', 3)
>>> next(i)
('zero', 0)
```

- ==Interesting fact==

```python
>>> d = {'one': 1, 'two':2}
>>> k = iter(d)
>>> next(k)
'one'
>>> d['zero'] = 0
>>> next(k)
RuntimeError: dictionary changed size during iteration
#Dictionary was mutated, if, this is the case you have to change the iterable
>>> d
{'one':1, 'two': 2, 'zero': 0}
>>> k = iter(d)
>>> next(k)
'one'
>>> next(k)
'two'
>>> d['zero'] = 5 #As long as the structure is intact
>>> next(k)
'zero'
>>>
```
#error `RuntimeError`

#### [[For statements]] and [[built-in functions]] for [[iterator]]

###### [[For statements]]

- ==For statements [[iterate]] over [[iterable]] values, they can also [[iterate]] over [[iterator]]s themselves==

```python
>>> r = range(3, 6)
>>> list(r)
[3, 4, 5]
>>> for i in r:
...		print(i)
...
3
4
5
>>> for i in r:
...		print(i)
...
3
4
5
>>> ri = iter(r) #Range iterator
>>> ri
<range_iterator object at 0x10d247a20> # Range iterator object not JUST A RANGE ITERATOR
>>>next(ri)
3
>>> for i in ri:
...		print(i)
...
4 #3 is used off in the line 19 and 20
5
>>>
```

- for statements also move the marker with in the iterator advancing all the way to the end of the sequence

```python
>>> r
range(3, 6)
>>> ri = iter(r)
>>> for i in ri:
... 	print(i)
...
3
4
5
>>> for i in ri:
... print(i)
...
```

Prints nothing  ==Because we reached the end==

- If I use an [[iterator]] in a [[For statements]] I can still go until the end but we cant use the [[iterator]] again to print anything.

###### [[built-in functions]] for [[iterator]]

- A great deal of processing of sequences another iterable values, uses [[built-in functions]]  that take one iterable value and give you back an iterator

==Many built-in Python sequence operations return iterators that compute results lazily== called [[Lazy computing]]

- [[map]](func, iterable): [[iterate]] over func(x)  for x in [[iterable]]
- [[filter]](func, iterable): [[iterate]] over x in iterable if func(x) **returns a true value**
- [[zip]](first_iter, second_iter): [[iterate]] over co-indexed (x, y) pairs, **Take two iterables**
- [[reversed]](sequence): [[iterate]] over x in a [[sequence]] in reverse order
- To view the contents of an [[iterator]], place the resulting elements into a [[container]]
  - list(iterable): Create a list containing all x in iterable
  - tuple(iterable): Create a tuple containing all x in iterable
  - sorted(iterable): Create a sorted list containing x in iterable

##### [[iter]] and [[next]]

```python

> > > bcd = ['b', 'c', 'd']
> > > [x.upper() for x in bcd]

['B','C','D']

> > > map(lambda x: x.upper(), bcd)

<map object at 0x10234343aef0> #Self explainatory, it gives a map object, which iterates over function(x) LAMBDA HERE for x in iterable

> > > m = map(lambda x: x.upper(), bcd)
> > > next(m)

'B'

> > > next(m)

'C'

> > > next(m)

'D'

> > > next(m)

StopIteration #Error`
```

#error `StopIteration`
- Let's see how got those results

```python
def double(x):
print('**', x, '=>', 2*x, '**')
return 2*x
print('hello world')`
```

    > > > map(double, [3,5,7])
    <map object at 0xsomethingf0>

    > > > m = map(double, [3,5,7])
    > > > next(m)

    ** 3 => 6 **
    6 #calculates only at for instance

    > > > next(m)

    ** 5 => 10 **
    10 #calculates only at THIS instance, again, doesn't move the marker any further

    > > > next(m)

    ** 7 => 14 **
    14 #AND FINALLY calculates only at THIS instance, again, doesn't move the marker any further``                

- ==Point here== is the func `double` is not applied to `[3, 5, 7]` immediately but instead applied trough [[Lazy computing]], or should I say **lazily**
  - [[map]] object when i call [[map]] can be passed to another [[sequence]] processing function

```python

> > > m = map(double, range(3, 7))
> > > f = lambda y: y >= 10 #Filter function
> > > t = filter(f, m)

#Calculates and returns all the values until it finds the true value, or satifies the condition of filter funtion lambda y

> > > next(t)

** 3 => 6 **
** 4 => 8 **
** 5 => 10 **
10 #Condition satisfied

> > > next(t)

** 6 => 12 **
12 #Condition satisfied, hence stops here itself.

> > > list(t)

[ ] #nothing left

> > > list(filter(f, map(double, range(3,7))))

** 3 => 6 **
** 4 => 8 **
** 5 => 10 **
** 6 => 12 **
[10,12] #Runs trough exhaustion, not lazy here.

> > > 
```

[[reversed]]

[[zip]]

[[generators]]
