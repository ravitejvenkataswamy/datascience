#inprogress 

### String Representations
- An object value should behave like the knd of dats it is meant to represent
- One aspect of that is that an object should know how to present itslef to the world, as a string or to produce a sting representation of itself.
- Strings are important: they represent language and programs
	- The description used are not just human languages but also in programming languages.
- In Python, built right into the extention of the language
	- all objects produce two string representations:
		1. the [[str]] is legible to humans
		2. the [[repr]] is legible to the Python Interpreter
			- That is its supposed to be an expression, an expression in Python language.
		- A lot of times both [[str]] and [[repr]] can be same, but not always.
			- Because Python was designed to be language that people could read, therefore the lot of the expressions have exactly the same form when the person might write when try to cummunicate the same idea
		- Sometimes these are different.
### Example: the [[repr]] String for an Object
- the repr function returns a Python expression (a sting) that evalutes to an equal object
- repr(object) `ris:ArrowRight`sting
	- Return the canonical string representation of the object. 
	- for most object types. `eval(repr(object)) == object.`
	- The result of repr is exactly what you see when the Python prints out before it evaluates

```shell
	>>> 12e12
	12000000000000.0
	>>> print(repr(12e12))
	12000000000000.0
```

> Plug-in: to execute python code: `{{py:print(i for i in range(10))}}`
> to evalutae python expression` {{eval: 12e12}}`

>`{{tool: u  "u" converts text to uppercase}},` you have define what it does in the .obsidian/scripts 

- Some objects do not have simple Python-readable string.
	- There's no way to write down an expression that very easily capture everything that some object is, or
	-  an expression for how to create something that's equal to the original object
		-  this is typically true of compound things, such as
			1. [[Function]]s or
			2. [[Class]]

		
```shell
>>> repr(min)
<built-in function min>
`{{py:print(repr(min))}}` used this to verify
```

- the `min` function that's built-in:
	- can't be written in single expression, so instead you see a proxy
`<built-in function min>`, the `<` & `>` (angled bracked) indicates that is a proxy and is, in fact, not a Python expression at all. It's just some standard.
- It's a human readable description but generating expression just didn't workout
- the `str` sting for an [[object]]:
	- Human interpretable strings are useful as well:
		- Fractions module part of standard module.
``` shell
>>> from fractions import Fraction
>>> half = Fraction(1, 2)
>>> repr(half)
'Fraction(1,2)'
>> str(half)
'1/2'
```

- `str` takes any object and gives you back a string, that string is human interpretable represenation of the original object

```ad-warning
The result of calling `str` on the value of an expression is what Python prints out when you call the `print` function
```



```shell
>> print(half)
1/2
```

- str(half) `ris:ArrowRight` `'1/2'` has quotes around it, because this is a `string`
- print(half) `ris:ArrowRight` `1/2` has no quotes around it, because this `print`ing a `string`.

![[Drawing 2021-06-04 20.55.56.excalidraw]]
  
  ```ad-warning
  - `eval( )` evaluates what's inside the quotes, eval always takes string, bytes and code object
  - only evalutes a valid Python expressions.
  ```
  
  
  ```shell
>>> s = 'Hello, World'
>>> s
'Hello, World'
>>> print(s)
Hello, World
>>> print(repr(s))
'Hello, World'
>>> print(str(s))
Hello, World
>>> str(s)
'Hello, World'
>>> str(1)
'1'
>>> str('hi')
'hi'
>>> str('hi,k')
'hi,k'
>>> repr(s)
"'Hello, World'"
>>> eval(repr(s))
'Hello, World'
>>> repr(repr(repr(s)))
'\\'"\\\\\\'Hello, World\\\\\\'"\\''
>>> eval(eval(eval(repr(repr(repr(s))))))
'Hello, World'
```
 
 ### Polymorphic Functions
 ##### Definition: 
 - A Polymorphic function is a function that applies to many (poly) types (also called forms(morphs)) of data 
 - str and repr are both polymorphic: they apply to any object
 - Fundamental idea: 
	 - is that `repr` just asks it's argument to display itself.
		 - and in Python, this is done using a special method called, it has a special name, because it corresponds to a built-in function
		 - The general idea, is that you can call a function that just asks the argument what to do, ceratinly applies beyond the Python language.
		 - `repr` in particular, invokes a zero-argument method `__repr__` on its argument, in order to get the repr string that it returns.
- We call repr on half

```shell
>>>half.__repr__()
'Fraction(1,2)'
```

- Or, we could invoke it's method, invoking method, gets looked up in the class, though its really the `Fraction` class that knows how to generate a string for a `Fraction(1, 2)`, its not the `repr` function
- Likewise, `str` invokes a zero-argument method `__str__` on its argument.
	- `__str__` another special method name
	- We could invoke this method directly if I wanted that would generate a `str` string for a fraction.
	- ==There's a really important idea here is:==
		- you could write a function like `str` or `repr` that actually doesn't have a logic at all, it just refers to the argument that comes in to decide what to do by invoking a method on it of a particular name.

### Implementing **repr** and **str**
- It's slightly more complicated than it's described, instead of invoking the repr on its argument, an instacne attribute called `__repr__` is ignored! 
- Only a class [[attribute]]s called `repr` are invoked by the `repr` function that's built-in.
- *Question*: How would we implement this behavior?
![[Screenshot 2021-06-05 at 9.23.11 AM.png]]
- The 3rd one manages to skip [[instance attribute]]s or ignore them by looking up the `type` of the argument, 
	- that gets you the class and
	- therefore asking for the `repr` attribute of the class is guaranteed to give you class attribute, 
	- now its class attribute that's a function and that function is a not valid method, because it is looked up in the class, so you have to explecitely pass in the `x` inorder to have this class attribute invoked on the particular argument that we are interested in.

- `str` is also complicated, even more complicated than repr.
	- An instance attribute called `__str__`  is ignored.
	- If no `__str__` attribute is found, uses **repr** string
	- *Question:* How would we implement this behavior?
		- **`str` is a class, not a function.**
			- When you are calling a `str` you are really calling a [[constructor]] for the built-in `string` `type` called `str`

```python 
class Bear:
	""" A Bear."""
	def __repr__(self):
		return 'Bear()'
oski = Bear()
print(oski)
print(str(oski))
print(repr(oski))
print(oski.__str__())
print(oski.__repr__())
```

```shell
Bear()
Bear()
Bear()
Bear()
Bear()
```


What happens if we define a 	`str` method as well
```python 
class Bear:
	""" A Bear."""
	def __repr__(self):
		return 'Bear()'
	def __str__(self):
		return 'a bear'
oski = Bear()
print(oski) #-> here
print(str(oski)) #-> here
print(repr(oski))
print(oski.__str__()) #-> here
print(oski.__repr__())
```

```shell
a bear
Bear()
a bear
a bear
Bear() 
```
In order to get more variety
```python
class Bear:
	""" A Bear."""
	def __init__(self):
		self.__repr__ = lambda: 'oski'
		self.__str__ = lambda: 'this bear'
	def __repr__(self):
		return 'Bear()'
	def __str__(self):
		return 'a bear'
oski = Bear()
print(oski) #-> same
print(str(oski)) #2 always the same as 1st one there's no real way to make them different
print(repr(oski)) 
```
the `repr` string ignores the instance attribute `self.__repr__ = lambda: 'oski'` and just uses the `__repr__` method, which is class attribute and also a function a we see a `Bear()` is returned.
Likewise, the `str`  **#2** string skips the instance attribute and goes striaght the to the class

```python
print(oski.__str__())
```
However,  
```python
print(oski.__repr__())

```


```shell
a bear
Bear()
a bear
a bear
Bear() 
