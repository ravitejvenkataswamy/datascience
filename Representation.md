#done 

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
print(str(oski)) 
```
```ad-note
` print(str(oski))`- always the same as 1st one there's no real way to make them different
```

```python
print(repr(oski)) 

```
```ad-note
the `repr` string ignores the instance attribute `self.__repr__ = lambda: 'oski'` and just uses the `__repr__` method, which is class attribute and also a function and so we see a `Bear()` is returned.
Likewise, the `str`  **#2** string skips the instance attribute and goes striaght the to the class
```

```python
print(oski.__str__())
```

```python
print(oski.__repr__())

```
```ad-note
However,  attribute look up in the conventional way gives us the functions, which when we call them `oski` and `this bear`
```

```shell
a bear
a bear
Bear()
this bear
oski
```

##### Let's try to recreate `repr` and `str` function:
```python
def repr(x):
	return type(x).__repr(x)
def str(x):
	t = type(x)
	if hasattr(t, '__str__'):
		return t.__str__(x)
	else:
		return repr(x)
```

```shell
a bear
a bear
Bear()
this bear
oski
```
we successfully recreated the `repr` and `str` functions

### Interfaces
- ==an important idea here==
- When we talk about [[Object-Oriented Programming]] in the first place, prof. [[John DeNero]] said that central to this metaphor was that objects would pass messages, that's how they would intereact.
- That mechanics in the languages is that they just look up attributes/methods on each other and that's how they communicate.
- So, here's the idea of *passing messages, passing the messages is the methphor* and *looking objects is actually what we do* in order to pass messages around.
- Now the attribute look-up rules are designed in a special way, they allow **different** data types to respond to the **same** messages, ***dispite*** having the **same attribute** name.
- A **shared messages**(attribute name) that exits in many different classes, that [[elicit]]s similar behavior from different object classes is a powerful method of [[Data abstraction|abstraction]]
	- That's what we call an interface
	- An interface is a set of shared messages, and specification that tell you what they are supposed to do, what they mean.
```ad-example
title: interfaces
- classes that implement `__repr__` and `__str__` methods and have those methods return Python-interpretable and human-readable strings respectively,
interface for producing string representations
- interpretors don't have to be built into the language although this one is 
```

```ad-note
if you ever define a bunch of classes that have the same method and those methods do the similar things and you have create an interface
```

#### demo

```python
class Ratio:
	def __init(self, n, d):
		self.numer = n
		self.denom = d
	def __repr__(self):
		return 'Ratio{0}, {1}'.format(self.numer, self.denom)
	def __str__(self):
		return '{0}/{1}'.format(self.number, self.denom)
```
```shell
>>> half = Ratio(1,2)
>>> print(half)
1/2 
>>> half
Ratio(1, 2)
>>> 
```

```ad-important
to print `Ratio(1, 2)` use formating
`'Ratio({0},{1})'.format(self.numer, self.denom)`
```

### Special Method Names
- cetain names are special because they have built-in behavior
- These names always start and end with two underscores, that has some interaction with object system in some way
```ad-example
- `__init__`- it's invoked automatically whenever an object is constructed, other than that it's just a regular method.
- `__repr__` - It's the method that gets invoked in order to produce a string that reperestns an object, it's the one that's used in an interactive Python session to display the value
- `__add__` - Two objects method, it's invoked to add one object to another 
- `__bool__` - is invoked to convert an object to `True` or `False`
- `__float__` - Tries to convert an object to a (float) real number

```

```shell
>>> zero, one, two = 0, 1, 2
>>> one + two
3
>>> bool(zero), bool(one)
(False, True)
>>> 
```

- you get the same behavior using these methods `ris:ArrowDown`

```shell
>>> zero, one, two = 0, 1, 2
>>> one.__add__(two)
3
>>>> zero.__bool__(), one.__bool__()
(False, True)
```

- It's another example i'm using an interface inorder to allow user defined objects to with the built in system, python is very extensible you can create a new class and be able to add instances of that class together using the `+` sign by overwriting the special function `add`

 - So, what happens when you have two instances of user defined class added together?
	 -  well, what happens is that invoke either the `__add__` or `__radd__` method. this `__radd__` actually perfoms the addition
```shell
>>> Ratio(1, 3) + Ratio(1, 6)
Ratio(1, 2)
>>> Ratio(1, 3).__add__(Ratio(1, 6))
Ratio(1, 2)
```

- The purpose of the `Ratio(1, 3).__add__(Ratio(1, 6))` is to allow ourselves to use definition snytax inorder to override what happens when you use a plus sign between two objects
```shell
>>> Ratio(1, 6).__radd__(Ratio(1, 3))
Ratio(1, 2)
```
![[Drawing 2021-06-06 20.00.37.excalidraw]]
- the difference between add and radd is the arguments are changed. though here the addition is cummilative, its irrelavant
- `__add__` and `__radd__` are equivalent

```ad-note 
title: Referances
collapse: open
[getpython3](http://getpython3.com/diveintopython3/special-method-names.html)
```

```ad-important 
title: Referances
[Python Docs](http://docs.python.org/py3k/reference/datamodel.html#special-method-names)
```

```python
class Ratio:
	def __init__(self, n, d):
		self.numer = n
		self.denom = d
	def __repr__(self):
		return 'Ratio({0},{1})''.format(self.numer, self.denom)
	def __str__(self):
		return '{0}/{1}'.format(self.numer, self.denom)
	def __add__(self, other):
		n = self.numer * other.demon + self.denom * other. numer
		d = self.denom * self.numer
		g = gcd(n, d)
		return Ratio(n//g, d//g) 
def gcd(n, d):
	while n!= d:
		n, d  = min(n, d), abs(n-d)
	return n
		
```

```shell
>>> gcd(12, 8)
4
>>> Ratio(1, 3) + Ratio(1, 6)
Ratio(1, 2)
>>> Ratio(1, 3) + 1
AttributeError
```

		
This can't be added with an integer so, we make:

```python
class Ratio:
	def __init__(self, n, d):
		self.numer = n
		self.denom = d
	def __repr__(self):
		return 'Ratio({0},{1})''.format(self.numer, self.denom)
	def __str__(self):
		if isinstance(other, int):
			n = self.numer + self.denom * other
			d = self.denom
		elif isinstance(other, Ratio):
			n = self.numer * other.demon + self.denom * other. numer
			d = self.denom * self.numer
		g = gcd(n, d)
		return Ratio(n//g, d//g) 
def gcd(n, d):
	while n!= d:
		n, d  = min(n, d), abs(n-d)
	return n
		
```
```shell
>>> Ratio(1, 3) + Ratio(1, 6)
Ratio(1, 2)
>>> Ratio(1, 3) + 1
Ratio(4, 3)
>>> 1 + Ratio(1, 3)
TypeError: unsupported operand type(s) for +: 'int' and 'Ratio'
```

This can be fixed with adding to the class Ratio:
`__radd__` = `__add__`

Hence
```shell
>>>> Ratio(1, 3) + Ratio(1, 6)
Ratio(1, 2)
>>> Ratio(1, 3) + 1
Ratio(4, 3)
>>> 1 + Ratio(1, 3)
Ratio(4, 3)
>>>> 
```
Fullfilled the interface for adding to a user defined class in the python language

- What happens if we add a floating value?
	-	Then n

```python
class Ratio:
	def __init__(self, n, d):
		self.numer = n
		self.denom = d
		
	def __repr__(self):
		return 'Ratio({0},{1})'.format(self.numer, self.denom)
		
	def __str__(self):
		if isinstance(other, int):
			n = self.numer + self.denom * other
			d = self.denom
		elif isinstance(other, Ratio):
			n = self.numer * other.demon + self.denom * other. numer
			d = self.denom * self.numer
		elif isinstance(other, float):
			return float(self) + other
		g = gcd(n, d)
		return Ratio(n//g, d//g)
	
	__radd__ = __add__
	
	def __float__(self):
		return self.numer/self.denom
		
def gcd(n, d):
	while n!= d:
		n, d  = min(n, d), abs(n-d)
	return n
		
```

```ad-note
title: Quesiton?
is `isinstance` an in-built function?
```

```ad-important
title: Ideas
- type dispatching: where you inspect the type of the arguments and decides to what to do
	- `if isinstance(other, int):`
		- `n = self.numer + self.denom * other`
		-	`d = self.denom`

- type coertion: When you take an object of one type and convert it into another type in order to be able to combine it with some other value
-	-  `	elif isinstance(other, float):`
		- `return float(self) + other`
			
```
	
```ad-note
title: Strategies
These are the two strategies that most programmers use
```

### Last drill
- ***Questoin***: Create a class Knagaroo with:
	- description:
		- Constructor insitialozes an instance
		-  variable namesd `poucn_contents` to an empty lis.
		-  `put_in_pouch` takes a sting as input and adds it to pouch_contents if it is not already in the pouch.
			-  If it's already in the pouch, print **"object already in pouch"**
		-  `__str__`: prints content of pouch. If the pouch is empty then print "The kangaroo's pouch is empty." 
		-  If the pouch is not empty then print "The kangaroo's pouch contains: [A, B, C]" ( where A, B, C are the cotents of the pouch)
		-  Write a short driver that tests your class
	-  solution:
```python
class Kangaroo():

    def __init__(self):
        pouch_contents = []

    def put_in_pouch(Some_string): #not sure yet
        if Some_string not in self.pouch_contents:
            self.pouch_contents.append(Some_string)
        else:
            print('object already in pouch')

    def __str__(self):
        if len(self.pouch_contents) == 0:
            print("The kangaroo's pouch is empty")
        else:
            print(self.pouch_contents)

```

```shell
 NameError: name 'put\_in\_pouch' is not defined
gives error, as put_in_pouch is not defined
```
#NameError
>That's why we have to use, `def put_in_pouch(self, Some_string)` ? **No**
>Still NameError persists, after adding self

```shell
>>> Kangaroo.put_in_pouch('something')

Traceback (most recent call last):

 File "<stdin>", line 1, in <module>

TypeError: put_in_pouch() missing 1 required positional argument: 'Some_string'

```
>This is what happens when you forget to create a class object

```ad-note
title: dont forget to create class object
      
```shell
>>> Kangaroo().put_in_pouch('somethign')

Traceback (most recent call last):

 File "<stdin>", line 1, in <module>

 File "/Users/superbeliever/Documents/Courses/CS61A Structure and Interpretation of Computer Programs/Week 20/Lecture20/drill.py", line 7, in put\_in\_pouch

 if Some\_string not in self.pouch\_contents:

AttributeError: 'Kangaroo' object has no attribute 'pouch_contents'
````

>let's see the output

Lecture solution
```python
class Kangaroo: #absolutely no brackets
    def __init__(self):
        self.pouch_contents = []

    def put_in_pouch(self, x):
        for i in range(len(self.pouch_contents)):
            if self.pouch_contents[i] == x:
                print("Already in pouch")
                return #i'm done, go home, return out of the function there's nothing to do here, boot out
        self.pouch_contents.append(x)
    def __str__(self):
        if(len(self.pouch_contents) == 0):
            return "The kangaroo's pouch is empty."
        else:
            return "The kangaroo's pouch contains: " + str(self.pouch_contents)

```

Slighlty modified:
```python
class Kangaroo: #absolutely no brackets
    def __init__(self):
        self.pouch_contents = [] #made mistake here

    def put_in_pouch(self, x):
        if x in self.pouch_contents:
            print("Already in pouch")
            return #i'm done, go home, return out of the function there's nothing to do here, boot out
        self.pouch_contents.append(x)
    def __str__(self):
        if(len(self.pouch_contents) == 0):
            return "The kangaroo's pouch is empty."
        else:
            return "The kangaroo's pouch contains: " + str(self.pouch_contents)

```

```shell
>>> k = Kangaroo()
>>> k.put_in_pouch('sdfsd')
>>> print(k)
The kangaroo's pouch contains: ['sdfsd']
>>> k.put_in_pouch('sdfsd')
Already in pouch
```