makeblank
    - Use this function

```python
def make_withdraw(balance):
			"""Return a withdraw function with BALANCE as its starting balance.
			>>> withdraw = make_withdraw(1000)
			>>> withdraw(100)
			900
			>>> withdraw(100)
			800
			>>> withdraw(900)
			'Insufficient funds'
			"""
	def withdraw(amount):
        nonlocal balance
        if amount > balance:
            return 'Insufficient funds'
        balance = balance - amount
        return balance
    return withdraw
```

- Problem Description:
	- Write a new function `make_bank`, which should create a bank account with value `balance` and should also return another function.
	- This new function should be able to **withdraw** and **deposit** money.
	- The second function will take in two arguments: `message` and `amount`
	- When the message passed in is `'deposit'`, the bank will deposit `amount` into the account.
	  - When the message passed in is `'withdraw'`, the bank will attempt to withdraw `amount` form the account.
	  - If the account does not have enough money for a withdrawal, the sting `'Insufficient funds'` will be returned.
	  - If the message passed in is neither of the two commands, the function should return `'Invalid message'` Examples are shown in the doctests.
- Version 4
 ```python
  def make_bank(balance):
  """Returns a bank function with a starting balance. Supports
  withdrawals and deposits.

  >>> bank = make_bank(100)
  >>> bank('withdraw', 40)    # 100 - 40

  60

  >>> bank('hello', 500)      # Invalid message passed in

  'Invalid message'

  >>> bank('deposit', 20)     # 60 + 20

  80

  >>> bank('withdraw', 90)    # 80 - 90; not enough money

  'Insufficient funds'

  >>> bank('deposit', 100)    # 80 + 100

  180

  >>> bank('goodbye', 0)      # Invalid message passed in

  'Invalid message'

  >>> bank('withdraw', 60)    # 180 - 60

  120
  """
	  def bank(message, amount):
	  nonlocal balance

			if message == 'withdraw':
				if amount > balance:
					return 'Insufficient funds'
				balance = balance - amount
				return balance
			elif message == 'deposit':
				balance = balance + amount
				return balance
			else:
			  return 'Invalid message'
		return bank #returning bank will store the data of balance
```

> `python3 ok -q make_bank`
        
		
- V4
 ```
  superbeliever@Ravitejs-MacBook-Air hw04 % python3 ok -q make_bank

# =====================================================================
Assignment: Homework 4
OK, version v1.18.1

    Running tests

    ---------------------------------------------------------------------
    Test summary
        1 test cases passed! No cases failed.
```

- Hints from video: ==No hints needed==
### Mind the strings to avoid spelling mistakes
#done

<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=def%20make_bank%28balance%29%3A%0A%20%20%20%20%22%22%22Returns%20a%20bank%20function%20with%20a%20starting%20balance.%20Supports%0A%20%20%20%20withdrawals%20and%20deposits.%0A%0A%20%20%20%20%3E%3E%3E%20bank%20%3D%20make_bank%28100%29%0A%20%20%20%20%3E%3E%3E%20bank%28'withdraw',%2040%29%20%20%20%20%23%20100%20-%2040%0A%20%20%20%2060%0A%20%20%20%20%3E%3E%3E%20bank%28'hello',%20500%29%20%20%20%20%20%20%23%20Invalid%20message%20passed%20in%0A%20%20%20%20'Invalid%20message'%0A%20%20%20%20%3E%3E%3E%20bank%28'deposit',%2020%29%20%20%20%20%20%23%2060%20%2B%2020%0A%20%20%20%2080%0A%20%20%20%20%3E%3E%3E%20bank%28'withdraw',%2090%29%20%20%20%20%23%2080%20-%2090%3B%20not%20enough%20money%0A%20%20%20%20'Insufficient%20funds'%0A%20%20%20%20%3E%3E%3E%20bank%28'deposit',%20100%29%20%20%20%20%23%2080%20%2B%20100%0A%20%20%20%20180%0A%20%20%20%20%3E%3E%3E%20bank%28'goodbye',%200%29%20%20%20%20%20%20%23%20Invalid%20message%20passed%20in%0A%20%20%20%20'Invalid%20message'%0A%20%20%20%20%3E%3E%3E%20bank%28'withdraw',%2060%29%20%20%20%20%23%20180%20-%2060%0A%20%20%20%20120%0A%20%20%20%20%22%22%22%0A%20%20%20%20def%20bank%28message,%20amount%29%3A%0A%20%20%20%20%20%20%20%20nonlocal%20balance%0A%0A%20%20%20%20%20%20%20%20if%20message%20%3D%3D%20'withdraw'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20amount%20%3E%20balance%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20'Insufficient%20funds'%0A%20%20%20%20%20%20%20%20%20%20%20%20balance%20%3D%20balance%20-%20amount%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20balance%0A%20%20%20%20%20%20%20%20elif%20message%20%3D%3D%20'deposit'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20balance%20%3D%20balance%20%2B%20amount%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20balance%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20return%20'Invalid%20message'%0A%0A%20%20%20%20return%20bank%0A%20%20%20%20%0Abank%20%3D%20make_bank%28100%29%0Abank%28'withdraw',%2040%29%20%20%20%20%23%20100%20-%2040%0Abank%28'hello',%20500%29%20%20%20%20%20%20%23%20Invalid%20message%20passed%20in%0A%0Abank%28'deposit',%2020%29%20%20%20%20%20%23%2060%20%2B%2020%0A&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=26&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
