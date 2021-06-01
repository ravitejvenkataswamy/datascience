- Methods is what represents the messages that an object will accepts
- They're just functions
```python
class Account:
	def __init__(self, account_holder):
    	self.balance = 0
    	self.holder = account_holder
        
    def deposit(self, amount):
      self.balance = self.balance + amount
      return self.balance
    
    def withdraw(self, amount):
      if amount > self.balance: #MIND THE SELF
        return 'Insufficient funds'
      else:
        self.balance = self.balance - amount
        return self.balance
```
- These `def` statements create function objects as always. but their names are bound as `attributes` of the `class`, and not bound in a particular [[frame]] 
- Therefore the Account class has three attributes
    - `__init__ , deposit, and withdraw`
### Invoking methods
    - All invoked methods have access to the object via the `self` parameter, and so they can all access and manipulate the object's state.
        - Look up it's balance, whatever.

```python
class Account:
		...
        
        def deposit(self, amount): #Defined with two arguments
          self.balance = self.balance + amount
          return self.balance
```

 [[dot expression]] automatically supplies the first argument to a method.

```shell
>>> tom_account = Account('Tom')
>>> tom_account = deposit(100) #Invoked with one argument
100
```

==Where's the second argument?==
        - First argument is `tom_account`
        - Second argument is `100`
 Dot Expressions
        - Objects receive messages via [[dot expression]].
        - [[dot expression]] accesses attributes of the instance **or** its class.
