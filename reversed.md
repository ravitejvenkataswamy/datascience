reversed
```python

> > > t = [1,2,3,2,1]
> > > t

[1,2,3,2,1]

> > > reversed(t)

<list_reverseiterator object at 0x10ehfassdf0>

> > > reversed(t) == t

False #You can't compare list and object iterator

> > > list(reversed(t))

[1,2,3,2,1]

> > > list(reversed(t)) == t

True
```