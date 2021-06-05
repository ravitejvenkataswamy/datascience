#done 

## Introduction in Lecture 19
- When it is applied appropriately, this can be of greater use, not otherwise. Often overused
- Recall [[attribute]]: Recalled from [[Inheritance]] perspective

```qrcode
Inheritence
```
[Lecture playlist](https://www.youtube.com/watch?v=m9wC1N9PtSw&list=PL6BsET-8jgYXpV7vl4Pvo25wh0FKRlecx)

[[ANTS]]: Ants Vs. SomeBees

### [[attribute]]
^d70870
- Recalled from [[Inheritance]] perspective
  - Terminology: [[attribute]]s, [[function]]s, and [[method]]s
    - All [[object]]s have attributes, which are name-value pairs
    - [[class]]es are objects too, so they have attributes
    - Instance attribute: attribute of an intsance
    - Class attribute: attribute of the class of an instance

![[Drawing 2021-06-01 23.56.20.excalidraw]]
- Functions aren't particular to [[Object-Oriented Programming]], but [[method]] are.
  - Method is function that's also a class attribure ^2072af

##### ==Python object system==

^e3ff36

1. Functions are objects
2. [[bound method]]s are also objects: a function that has its first paremeter [[self]] already bound to an instance.
3. [[dot expression]]s evalute to bound methods for class attributes that are functions

`<instance>.<method_name>` is a very common pattren
where you put some <instance> here before the (dot) and after the dot you have a method name; then that method is function named with the instance filled in as self parameter

A quick review on how [[dot expression]]s work

```shell
	<instance>.<method_name>
```

#### To evaluate a [[dot expression]]
- Evaluate the `<expression>`  to the left of the dot, which yields the [[Object]] of the [[dot expression]]
- `<name>`  is matches against the instance attributes of that object;
  if an attribute with the name exists, its value is returned (value in the sense value of the whole [[dot expression]])
- If not, <name> is looked up in the class, which yields a [[class]] attribute value.
- That [[attribute]] value is returned unless it is a function, in which case a [[bound method]] is returned instead.
  a slighly different version of function, where you get the function, with it's first parameter bound already to the object of the [[dot expression]]

![[attribute assignment#^f94e9b]]

## [[Inheritance]]

![[Inheritance#^e3ff36]]

- a feature that exists almost in every programming language.
- Inheritance is a method for relating (multiple) [[class]]es together
  Becuse not every class exits in isolatoin, sometime one is just similar to another we just want express their relations

```ad-note
collapse: open
A common use: Two similar classes differ in their degree of specilaization

```

The [[specialized class]] may have the same attributes as the general class, along with some special-case behavior.

```python
		class <Name>(<base class>):
			<suite>
```

`<base class>` is where the `<class Name>` inherits from

- Conceputally, the new subclass (`<class Name>`) "shares" attributes with its base class.
- The subclass (`<class Name>`)  may _override_ certain inherited attributes.
  in order to change the behaviour slighly, but anything that not changes stays the same.
- Using inheritance, we implement a subclass by specifying its _differences_ form the base class.

### Example

- A `CheckingAccount` is a specialized type of Account.

```shell
>>> ch = CheckingAccount('Tom')
>>> ch.interest # Lower interest rate for checking accounts
0.01
>>> ch.deposit(20)
20
>>> ch.withdraw(5) # Withdrawals incur a $1 fee
14
```

_Most_ behavior is shared with the base class `Account`

```python
class CheckingAccount(Account):
	""" A bank account that charges for withdrawals. """
		withdraw_fee = 1
		interest = 0.01
		def withdraw(self, amount):
				return Account.withdraw(self.amount + self.withdraw_fee) #adding the withdraw_fee for as usual withdraw function form `Account`
```

^12176e

- How do we do the withdraw part?
  - We refer to the method on the base called Account.withdraw,
  - since we are looking it up on a class as opposed to on an instance we are _**not**_ going get  [[bound method]] back
  - the main withdraw function will be taken from `Account`
  - we need to specify [[self]] ourselves, because it not a [[bound method]]

We don't need to say anything about `__int__` or `deposit` attributes

### Looking up Attribute Names on Classes

**- Base class attributes *aren't copied* into sub-classes!**
#### To look up a name in a class.
1. If it names an [[attribute]] in the class, return the attribute value.
2. Otherwise, look up the name in the [[base class]], if there is one.
	1. Goes to point `1.` we doing it recursively
	2. Otherwise, we loop up in the name in the base class of a base class

```shell
>>> ch = CheckingAccount('Tom')
```
Calls `Account.__init__`, First we look up in the CheckingAccount, since the CheckingAccount doesn't have it's own `__init__` method, we will check in it's base class Account.

```shell
>>> ch.interest #Found in CheckingAccount
0.01
```

Well, there's a special interest rate for checking account

``` shell
>>> ch.deposit(20) #Found in Account
20
```
All the depositing happens from the `Account`, here's what we do:
1. We try to evaluate the expression, which is a dot expression `ch.deposit(20)
	1.  which means we look up deposit on this `CheckingAccount` first, we check in the instance, no deposit there.
	2.  We check in the `CheckingAccount` `class`, no [[attribute]] `deposit` there.
1. Then we check in the `Account` `class`, theres is [[method]] called `deposit` , we get back the [[bound method]] here.
```shell
>>> ch.withdraw(5) 
15
```
We found this in `CheckingAccount` itself
###### Example

![[attribute#^c2537e]]

``` python
class CheckingAccount(Account):
	interest = 0.01
	withdraw_fee = 1
	def withdraw(self, amount):
		return Account.withdraw(self, amount + self.withdraw_fee)
```

here the `Account.withdraw(self, amount + self.withdraw_free)` , the self here is from the `Account` class

--- 
*Coping the withdraw may seem approriate as long as you don't makes changes in the base class, for which the changes wont be reflected in the inherited class and it also increases code redundency hence memory* ^bc43cd
``` python
class CheckingAccount(Account):
	interest = 0.01
	withdraw_fee = 1
	def withdraw(self, amount):
		amount = amount + 1
		if amount > self.balane:
			return 'Insufficient funds'
		self.balance = self.balance - amout
		return self.balance
```

^93eb5e

---
```shell
>>> a = Account('John')
>>> b = CheckingAccount('Jack')
>>> a
<__main__.CheckingAccount object at 0x23434792>
>>> a.balance
0
>>> b.balance
0
>>> a.deposit(100)
100
>>> b.deposit(100)
100
>>> a.withdraw(10)
90
>>> b.withdraw(10)
89
>>
```

## Object-Oriented Design

^da1658
- Designing [[Object-Oriented Programming|Object-Oriented Programs]]
- Some of the choices you will encounter and some guidence to come to a useful solution
 ### Designing for Inheritance
 ![[Inheritance#^12176e]]
1. Don't repear yourself; use exisiting implemenations.

![[Inheritance#^bc43cd]]
Like this one.
![[Inheritance#^93eb5e]]
 
2. [[attribute]]s that have been overridden are still accessible via class objects.
 	- to override an [[attribute]] means that in the sub-class, you are giving the an attribute the same name as exists in the base class.
		- example `withdraw` exists in CheckingAccount which also exists in the Base class `Account`
		- Even thorugh we have overridden that name, meaning that CheckingAccount will call it's withdraw, instead of `Account withdraw` / `original withdraw` we call still access and use them using the class [[Object]]
		- `Account.withdraw` will give us original [[method]] as opposed to this new one for CheckingAccount
		- We can still defer to the old logic with a small change by addding `withdraw_fee`
		-  ![[Inheritance#^12176e]]
3. Look up attributes on instances whenever possible.
	- When we compute the total amount that we are going to withdraw from the CheckingAccount we have several opitons here
		1. `amount + 1` ; hard coding with the withdraw fee but then we could never change it
		2. `amount + CheckingAccount.withdraw_fee`; which get the attribute `withdraw_fee`, but it wouldn't allow for the fact that some `CheckingAccount`s will have a speacial `withdraw_fee`
		3. The best way to do this is to is to look up withdraw_fee on the instance itself.  `self.withdraw_fee`
			1.  `Account.withdraw` `ris:ArrowRight` Attribute loop-up on base class
			2.  `self.withdraw_fee` `ris:ArrowRight` Preferred to CheckingAccount.withdraw_fee to all for specialized accounts for futher development. Like adding speacial `withdraw_fee` for particular type of account somthing like, `CheckAccountPWD.withdraw_fee = 0`
 ### Inheritance and [[Composition]]
 - When to use inheritance and when to use [[composition]]
- ![[Composition#^860264]]
- [[Object-Oriented Programming]]shines when we follow the metaphor, that is to retreat objects like real things in the world, which helps us think about them clearly.
- [[Inheritance]] is best for respresenting  **is-a**  relationships
	- Checking account is a type of account
		- `checking account is a specific type of account`
		- So, `CheckingAccount` inherits form `Account`.
- [[Composition]] is best for represting **has-a** relationships. 
	-  ![[Composition#^bf048a]]
	-  E. g., a bank has a collection of bank accounts that it manages.
	-  So, A Bank has a list of accounts as an [[attribute]]s.
		-  but a `Bank` won't inherit form an `Account` and an `Account` won't inherit from a `Bank`
		-  They're related, one has another has an attribute, but they're not related according to inheritance
 
![[attribute#^c2537e]]
 ![[Inheritance#^12176e]] 
 Bank~~()~~ ==won't== inherit from an account, because a Bank **has** accounts.
 
``` python
class Bank: 
""" A bank **has** accounts.
>>> bank = Bank()
>>> john = bank.open_account('John', 10)
>>> jack = bank.open_account('Jack', 5, CheckingAccount)
>>> john.interest
0.02
>>> jack.interest
0.01
>>> bank.pay_interest()
>>> john.balance
10.2
>>> bank.too_big_to_fail()
True
"""
```
Bank is constructed with no arguments

```python
def __init__(self):
	self.accounts = [] We are gonna have to remember what accounts are being held by that bank
def open_account(self, holder, amount, kind = Account): #method
	account = kind(holder) #Kind is bound to Account method
	account.deposit(amount)
	self.accounts.append(account)
	return account
def pay_interest(self):
	for a in self.accounts:
		a.deposit(a.balance * a.interest)
		
def pay_interest(self):
	for a in self.accounts:
		a.deposit(a.balance * a.interest)
		
def too_big_to_fail(self):
	return len(self.accounts) > 1
``` 

### Attributes Lookup Practice

#### Inheritance and Attribute Lookup
``` python
class A:
	z = -1
	def f(self, x):
		return B(x - 1)

class B(A):
	n = 4
	def __init__(self, y):
		if y:
			self.z = self.f(y)
		else:
			self.z = C(y + 1)
			
class C(B):
	def f(self, x):
		return x


a = A() `#composition`
b = B(1) `#passed 1 to B's attribute y` b is an object, a class instantiation
b.n = 5
```



``` shell
>>> C(2).n
4
>>> a.z == C.z
False

>>>> a.z == b.z
False

```
Which evaluates to an integer?
- [x] b.z
- [x] b.z.z
- [ ] b.z.z.z # only this evaluates to an interger.
- [x] b.z.z.z.z
- [x] None of these

![[Drawing 2021-06-02 21.04.13.excalidraw]]

After watching video.

![[Drawing 2021-06-03 00.07.03.excalidraw]]
	

	
### Multiple Inheritance
	
```python
class SavingsAccount(Account):
	deposit_fee = 2
	def deposit(self, amount):
			return Account.deposit(self. amount - self.deposit_fee) 
```
- A class may inherit from multiple base classes in Python.
- CleverBank marketing executive wants:
	- Low interest rate of 1%e
	- A $1 fee for withdrawals
	- A $2 fee for deposits
	- A free dollar when you open your account
	
	
``` python
class AsSeenOnTVAccount(CheckingAccount, SavingsAccount):
		def __init__(self, account_holer):
				self.holder = account_holder
				self.balance = 1 # A free dollar!
```
	
	![[Drawing 2021-06-03 22.47.56.excalidraw]]
	
### Resolving Ambiguous Class Attribute Names
	
![[Drawing 2021-06-03 22.55.13.excalidraw]]
	
### Complicated Inheritance.
- the multiple inhertiance tends to make programs complicated.
- it should be used very rarely indeed.
- if you wanna design clear programs


#### Biological Inheritance.
![[Screenshot 2021-06-03 at 11.15.13 PM.png]]
	
This tree is growing at exponential rate, which implies there are many many more people in previous generation than there are now. ~~Not True~~
		- Which says we had more population in previous generations, which obviously is not the case.
		- **there must be some over lap**
![[Screenshot 2021-06-03 at 11.20.57 PM.png]]
	
```ad-warning
collapse: open
be very careful with multiple inheritance

```