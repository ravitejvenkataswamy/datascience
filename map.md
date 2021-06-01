### A beautiful relation between map and lambda
`map(func, iterable)`
Here's an example:
```python
bcd = ['b', 'c', 'd']
map(lambda x: x.upper(), bcd)
<map object at 0x10345483>
m = map(lambda x: x.upper(), bcd)
next(m)
'B'
next(m)
'C'
next(m)
'D'
next(m)
StopIteration
```

##### Why the name `map?` #curious_question 

#error `StopIteration`

### Let's see how map works
``` 
def double(c):
		print('Doubles', c, '=>', 2 * c )
	
```


`on shell`

m = map(double, \[1, 2, 3, 4\])

\>>> next(m)

Doubles 1 => 2

\>>> next(m)

Doubles 2 => 4

--- 
      

\>>> m = map(double, range(3,7))

\>>> f = lambda y: y > = 10

 File "<stdin>", line 1

 f = lambda y: y > = 10

 							^

SyntaxError: invalid syntax
	`SyntaxError` #error > = is not valid (No space)
[[filter]]
\>>> f = lambda y: y >= 10

\>>> filter(f, m)

<filter object at 0x104402970>

\>>> t = filter(f, m)

\>>> t

<filter object at 0x104402700>

\>>> next(t)

Doubles 3 => 6

Traceback (most recent call last):

 File "<stdin>", line 1, in <module>

 File "<stdin>", line 1, in <lambda>

TypeError: '>=' not supported between instances of 'NoneType' and 'int'
#forgotreturn hence cannot compare between `NoneType` and `int`
```python
def double(c):
		print('Doubles', c, '=>', 2 * c )
		return 2 * c
```

\>>> next(t)

Doubles 4 => 8

Traceback (most recent call last):

 File "<stdin>", line 1, in <module>

 File "<stdin>", line 1, in <lambda>

TypeError: '>=' not supported between instances of 'NoneType' and 'int'

---
