---
date updated: '2021-05-29T16:04:13+05:30'

---

- ` <expression> . <name>  `
- The `<expression>` can be any valid Python expression.
- The `<name>` must be a simple name.
- Evaluates to the value fo the attribute **looked up** by `<name>` in the object that is the value of the `<expression>`
  - Looked up by:
    - You look in the instance and see is this `<name>` bound there, if not then you check the class
- `tom_account.deposit(10)`
  - This is a call expression with a compound operator, the compound operator is a dot expression and what it does is goes and finds the `deposit` method (which is actually part of `Account` `class` that `tom_account` is an instance of) of `tom_account`
  - the `tom_account.deposit`(dot expression) evaluates to  to function and then we will call it on `10`

```python
class Account:
	def __init__(self, account_holder):
		self.balance = 0
		self.holder = account_holder

    def deposit(self, amount):
    '''Add amount to balance'''
      self.balance = self.balance + amount
      	return self.balance

    def withdraw(self, amount):
      '''Subtract amount from balance form this account if 			the funds are sufficient'''
      if amount > self.balance: #MIND THE SELF
        return 'Insufficient funds'
      else:
        self.balance = self.balance - amount
        return self.balance
```
      
- Output

```
>>> Account
<class '__main__.Account'>
>>> john = Account('John') #Object instantiation
>>> john
<___main__.Account object at 0x1006f2210>
>>> type(john)
<class.__main__.Account'>
>>> john.balance
0
>>> john.holder
'John'
>>> john.deposit(10)
10
>>> john.deposit(10)
20
>>> john.deposit(10)
30
>>> john.balance
30
>>> john.withdraw(30)
0
>>> john.withdraw(30)
'Insufficient funds'
```
