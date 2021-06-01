Class Attributes
- Class attributes are 'shared' across all instances of a class because they are attributes of the class, not the instance.
 ```python
class Account:
interest = 0.2 #A class attribute
def **init**(self, account_holder):
self.balance = 0
self.holder = account_holder

#Additional methods would be defined here.
```
- Terminal
```
>>> tom_account = Account('Tim')
>>> jim_account = Account('Jim')
>>> tom_account.interest
0.02
>>> jim_account.interest
0.02
```

- ==Interest is not part of the instance that was some how copied form the class==
- It's important that this stays this way because, if we need to update the interest, the whole class should be affected, not just one instance.