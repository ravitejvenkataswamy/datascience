---
date updated: '2021-06-02T01:56:57+05:30'

---

- Attribute assignment statements; change the values that are

bound to attribute name with an [[object]] or a [[class]].

- So, you can assign to attributes, [[assignments statements]] with a [[dot expression]] on their ==left-hand side== are _attribute assignment statements_, so affect attributes for the object of that dot expression.

1. - If the object is an instance, then assignment sets an [[instance attribute]] ^426e81
2. If the object is a [[class]], then assignment sets a [[class attribute]]

```python
class Account:
	interest = 0.02
	def __init__(self, holder):
		self.holder = holder
		self.balance = 0
	...
tom_account = Account('Tim')
```

^8c108e

`interest` is already a [[class attribute]] ^336c88

Where as `holder` and `balance` are [[instance attribute]]s
Because they're set on the new instance created and passed to [[init]]
`Account` is class and `tom_account` is an _instance_ of the class ^c440f1

if I say `tom_account.interest` = 0.08
That's setting for an [[instance attribute]] because the object of the dot expression is an instance of the class `Account` ^c043bc

<expression>.<method> == <tom_account.interest> = 0.08
here the <expression> (tom_account) evalutes to an object of the class `Account`; ==Where as the whole thing `tom_account.interest` doesn't lookup `interest` on that object(tom_account) and/or go find it in the class==, instead we just direclty assign to the attribute of the object(tom_account) **This is attribute assignment**
	
	Attribute assignment statement adds or modifies the attributes named "interest" of tom_account
	 
	in this case the instance didn't have an interest attribute before and so the  [[assignments statements]] will add one.

 where as for [[Class Attributes]]
	[[Class Attributes]] assignment: `Account.interest = 0.04`

Object of this [[dot expression]] is a class called `Account` 
This will go on and change the interest *attribute of the class *`Account`

```shell
	>>> jim_account = Account('Jim')
	>>> tom_account = Account('Tom')
	>>> tom_account.interest
	0.02
	>>> jim_account.interest
	0.02
	>>> tom_account.interest
	0.02
```
	
If we set  
```shell
	>>> Account.interest = 0.04
```
if will also refelect the changes in the [[instance attribute]], a particular instance attribute already has a interest variable inside itself.

```shell
>>> tom_account.interest
0.04
>>> jim_account.interset
0.04
```

Where as if we set 

```shell
>>> jim_account.interest = 0.08 
```
this is called instanace [[attribute assignment]]


```shell
>>> jim_account.interest
0.08
tom_account.interest
0.04

```
giving a spcial intereset to jim
	
```shell
Account.interest = 0.05
```
Setting class attribute interest to someother value, say, 0.05

	
```shell

>>> tom_account.interest
0.05
>>> jim_account.interest
0.08

```
	
```ad-summary
[[attribute assignment]]: After assigning to the special case, when you *change* the class attribute, you will **still** have the special case saved in the [[instance attribute]] in this case `jim_account.interest` remains unchanged with respect to changes in the class attribute
```

^f94e9b

