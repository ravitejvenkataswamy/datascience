- A class combines (and abstracts) data and functions
- An object is an instantiation of a class
- What class does is putting all these pieces together, meaning storing of information, data and [[functionality]] on that data
- 

- A class combines (and abstracts) data and functions
- Is something that combines and abstracts out [[data]] and [[functionality]]

- A class serves as a template for its instances. 
- Idea
	-  All bank accounts have a balance and an account holder; the Account class should add those arrtibutes to each newly created instances.
	-  ```
    >>> a = Account('Jim')
    >>> a.holder
    Jim
    >>> a.balance
    0

	- All bank accounts should have "withdraw" and "deposit" behaviours that all work in the same way.
	  ```
	  >>> a.deposit(15)
	  15
	  >>> a.withdraw(10)
	  5
	  >>> a.balance
	  0
	  >>> a.withdraw(10)
	  'Insufficient fund'


- Some `a.deposit(15)` of them look like a call expression and some `a.balance` act like they access a value.
  - We have to make sure all account share the same `deposit` and `withdraw` [[functionality]]

- Class Statements
  - Will let you create any `type` of data you want
    class <name>: <suite>

- A class statement creates a new class and binds that class to <name> in the first [[frame]] of the current [[environment]]
  - Assignment & def statements in `<suite>` create [[attribute]]s of the class **(not names in frames)**

It's a convention to use Capital letter
the beginning letter of the name of the class
``` 
Class Clown
... 	nose = 'big and red'
...		def dance():
...			return 'No thanks'
...

>>> Clown.nose #Notice the dot operator
'big and red' 
>>> Clown.dance()
'No thanks'
>>> Clown
<class '__main__.Clown'>
```

- Object Construction
  - Idea:
    - All bank accounts have a `balance` and an account `holder`;
    - The `Account` `class` should add those attributes to each of its instances
    - `a= Account('Jim')`
  - When a class is called:
    - 1. A new instance of that class is created: `blank`
      - Initially it'll be blank, it's up to the class to fill it
    - 2. The [[special function]] names [[**init**]] method of the class is called with the new object as its first argument (name [[self]]), along with any additional provided in the call expression.

```python

class Account:
def __init__(self, account_holder): #the self will fill the blank instance that is created, while creating the class
self.balance = 0
self.holder = account_holder
```

a= Account('Jim') Jim will take place of account_holder, even though it's not the first place

- `   balance: 0 holder: 'Jim'        `
  - This blank instance is filled with this^

```
>>> a = Account('Jim')
>>>a.holder
'Jim'
>>> a.balance
0
```

- Object Identity
  - Every object that is an instance of a user-defined class has a unique identity:

```python
>>> a = Account('Jim')
>>> b = Account('Jack')
```

Every call to Account creates a new Account instance. There is only one Account class.

    >>> a.balance
    0
    >>> b.holder
    'Jack'

 Identity operators `is` and `is not` test if two expressions evaluate to the same object:
  ```
  >>> a is a
  True
  >>> a is not b
  True   
  ```
  
==Binding an object to a new name using assignment does not create a new object==
```
>>> c = a
>>> c is a
True
```

[[How to create class]]
  