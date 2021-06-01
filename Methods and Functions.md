
- Methods is an attribute that is a function
- Python distinguishes between:
- __Functions__, which we have been creating since the beginning of the courese, and
- [[bound method]]s, which couple together a `function` and the `object` on which the method will be invoked.
- #### Object + Function = Bound Method
```python
>>> type(Account.deposit)
<class 'function'> #this take 2 arguments, the objects that i'm depositing into, and the amount that i want to deposit
>>> type(tom_account.deposit) #this is looking up deposit on an instance tom_account of class Account,
#we get a method. Which means it has taken a deposit funciton and bound it together with tom_account
#which wil be passed as a first argument when we actually call the funcion
<class 'method'>

>>> Account.deposit(tom_account, 1001) #when we access the function directly form the class we need to pass in two arguments, one was called self, and another one was called amount
1001
>>> tom_account.deposit(1000) #If I startoff with tom_account and I lookup using (dot expression) what I get back is a method, see line 6
2011

```

- `line 8 &10` A `method` is different than a `function` in the sense the first `argument` is already fill in with `tom_account`