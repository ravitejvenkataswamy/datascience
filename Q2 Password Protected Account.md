
[ ] Question 2: **Password Protected Account** #done   [[nonlocal]]
Previous queston:  [[Q1 makeblank]]

###### Problem description
Write a version of the `make_withdraw` function show in the previous question that returns password-protected withdraw functions.
That is, `make_withdraw` should take a password argument(a string) in addition to an initial balance.
- The returned function should take two arguments: an ==amount to withdraw== and a ==password==
- A password-protected `withdraw` function should only process withdrawals that include a password that matches the original. Upon receiving a incorrect password, the function should:
	1. Store that incorrect password in a list, and 
	2. Return the string 'Incorrect password'
			- If withdraw function has been called three times with incorrect passwords `<p1>`, `<p2>`, and `<p3>`, then it is frozen.
All subsequent calls to the function should return:
> `"Frozen account. Attempts: [<p1>, <p2>, <p3>]"`
###### structure
```python
    def make_withdraw(balance, password):
        """Return a password-protected withdraw function.

        >>> w = make_withdraw(100, 'hax0r')
        >>> w(25, 'hax0r')
        75
        >>> error = w(90, 'hax0r')
        >>> error
        'Insufficient funds'
        >>> error = w(25, 'hwat')
        >>> error
        'Incorrect password'
        >>> new_bal = w(25, 'hax0r')
        >>> new_bal
        50
        >>> w(75, 'a')
        'Incorrect password'
        >>> w(10, 'hax0r')
        40
        >>> w(20, 'n00b')
        'Incorrect password'
        >>> w(10, 'hax0r')
        "Frozen account. Attempts: ['hwat', 'a', 'n00b']"
        >>> w(10, 'l33t')
        "Frozen account. Attempts: ['hwat', 'a', 'n00b']"
        >>> type(w(10, 'l33t')) == str
        True
        """
        "*** YOUR CODE HERE ***"
```
- and given functions: None

__Hints__:
- You can use the `str` function to turn a list into a string.
- For example, for a list `s = [1, 2, 3]`, the expression `"The list s is: " + str(s)` simplifies to `"The list s is: [1, 2, 3]"`.
- ==The incorrect passwords may be the same or different:==

- ### Code attempt after hints


- V2
```python
    def make_withdraw(balance, password):
        """Return a password-protected withdraw function.

        >>> w = make_withdraw(100, 'hax0r')
        >>> w(25, 'hax0r')
        75
        >>> error = w(90, 'hax0r')
        >>> error
        'Insufficient funds'
        >>> error = w(25, 'hwat')
        >>> error
        'Incorrect password'
        >>> new_bal = w(25, 'hax0r')
        >>> new_bal
        50
        >>> w(75, 'a')
        'Incorrect password'
        >>> w(10, 'hax0r')
        40
        >>> w(20, 'n00b')
        'Incorrect password'
        >>> w(10, 'hax0r')
        "Frozen account. Attempts: ['hwat', 'a', 'n00b']"
        >>> w(10, 'l33t')
        "Frozen account. Attempts: ['hwat', 'a', 'n00b']"
        >>> type(w(10, 'l33t')) == str
        True
        """
        "*** YOUR CODE HERE ***"
```

- Terminal outputs:
 V3
```       
superbeliever@Ravitejs-MacBook-Air hw04 % python3 ok -q make_withdraw
=====================================================================
Assignment: Homework 4
OK, version v1.18.1
=====================================================================
  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running tests

\---------------------------------------------------------------------
Test summary
 1 test cases passed! No cases failed.
``` 

> python3 ok -q make_withdraw

<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=def%20make_withdraw%28balance,%20password%29%3A%0A%20%20%20%20%22%22%22Return%20a%20password-protected%20withdraw%20function.%0A%0A%20%20%20%20%3E%3E%3E%20w%20%3D%20make_withdraw%28100,%20'hax0r'%29%0A%20%20%20%20%3E%3E%3E%20w%2825,%20'hax0r'%29%0A%20%20%20%2075%0A%20%20%20%20%3E%3E%3E%20error%20%3D%20w%2890,%20'hax0r'%29%0A%20%20%20%20%3E%3E%3E%20error%0A%20%20%20%20'Insufficient%20funds'%0A%20%20%20%20%3E%3E%3E%20error%20%3D%20w%2825,%20'hwat'%29%0A%20%20%20%20%3E%3E%3E%20error%0A%20%20%20%20'Incorrect%20password'%0A%20%20%20%20%3E%3E%3E%20new_bal%20%3D%20w%2825,%20'hax0r'%29%0A%20%20%20%20%3E%3E%3E%20new_bal%0A%20%20%20%2050%0A%20%20%20%20%3E%3E%3E%20w%2875,%20'a'%29%0A%20%20%20%20'Incorrect%20password'%0A%20%20%20%20%3E%3E%3E%20w%2810,%20'hax0r'%29%0A%20%20%20%2040%0A%20%20%20%20%3E%3E%3E%20w%2820,%20'n00b'%29%0A%20%20%20%20'Incorrect%20password'%0A%20%20%20%20%3E%3E%3E%20w%2810,%20'hax0r'%29%0A%20%20%20%20%22Frozen%20account.%20Attempts%3A%20%5B'hwat',%20'a',%20'n00b'%5D%22%0A%20%20%20%20%3E%3E%3E%20w%2810,%20'l33t'%29%0A%20%20%20%20%22Frozen%20account.%20Attempts%3A%20%5B'hwat',%20'a',%20'n00b'%5D%22%0A%20%20%20%20%3E%3E%3E%20type%28w%2810,%20'l33t'%29%29%20%3D%3D%20str%0A%20%20%20%20True%0A%20%20%20%20%22%22%22%0A%20%20%20%20tried_passwords%20%3D%20%5B%5D%0A%20%20%20%20%23Need%20to%20use%20higher%20order%20funtion%0A%20%20%20%20def%20private_account_withdraw%28amount,%20entered_password%29%3A%0A%20%20%20%20%20%20%20%20%23nonlocal%20password%20%23we%20need%20to%20know%20the%20password%20to%20check%20it's%20if%20it%20matches%20only,%20so%20therefore%20we%20don't%20need%20to%20change%20it.%0A%20%20%20%20%20%20%20%20nonlocal%20balance%0A%20%20%20%20%20%20%20%20nonlocal%20tried_passwords%0A%0A%0A%20%20%20%20%20%20%20%20if%20entered_password%20%3D%3D%20password%3A%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20amount%20%3E%20balance%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20'Insufficient%20funds'%0A%20%20%20%20%20%20%20%20%20%20%20%20balance%20%3D%20balance%20-%20amount%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20balance%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20tried_passwords.append%28entered_password%29%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20len%28tried_passwords%29%20%3E%202%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20%22Frozen%20account%22%20%2B%20str%28tried_passwords%29%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20'Incorrect%20password'%0A%20%20%20%20return%20private_account_withdraw%0A%20%20%20%20%0Aw%20%3D%20make_withdraw%28100,%20'hax0r'%29%0Aw%2875,%20'a'%29%0A%0Aw%2810,%20'hax0r'%29%0Aw%2820,%20'n00b'%29%0A%0Aw%2810,%20'hax0r'%29%0Aw%2810,%20'l33t'%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

##### Final code
<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=def%20make_withdraw%28balance,%20password%29%3A%0A%20%20%20%20%22%22%22Return%20a%20password-protected%20withdraw%20function.%0A%0A%20%20%20%20%3E%3E%3E%20w%20%3D%20make_withdraw%28100,%20'hax0r'%29%0A%20%20%20%20%3E%3E%3E%20w%2825,%20'hax0r'%29%0A%20%20%20%2075%0A%20%20%20%20%3E%3E%3E%20error%20%3D%20w%2890,%20'hax0r'%29%0A%20%20%20%20%3E%3E%3E%20error%0A%20%20%20%20'Insufficient%20funds'%0A%20%20%20%20%3E%3E%3E%20error%20%3D%20w%2825,%20'hwat'%29%0A%20%20%20%20%3E%3E%3E%20error%0A%20%20%20%20'Incorrect%20password'%0A%20%20%20%20%3E%3E%3E%20new_bal%20%3D%20w%2825,%20'hax0r'%29%0A%20%20%20%20%3E%3E%3E%20new_bal%0A%20%20%20%2050%0A%20%20%20%20%3E%3E%3E%20w%2875,%20'a'%29%0A%20%20%20%20'Incorrect%20password'%0A%20%20%20%20%3E%3E%3E%20w%2810,%20'hax0r'%29%0A%20%20%20%2040%0A%20%20%20%20%3E%3E%3E%20w%2820,%20'n00b'%29%0A%20%20%20%20'Incorrect%20password'%0A%20%20%20%20%3E%3E%3E%20w%2810,%20'hax0r'%29%0A%20%20%20%20%22Frozen%20account.%20Attempts%3A%20%5B'hwat',%20'a',%20'n00b'%5D%22%0A%20%20%20%20%3E%3E%3E%20w%2810,%20'l33t'%29%0A%20%20%20%20%22Frozen%20account.%20Attempts%3A%20%5B'hwat',%20'a',%20'n00b'%5D%22%0A%20%20%20%20%3E%3E%3E%20type%28w%2810,%20'l33t'%29%29%20%3D%3D%20str%0A%20%20%20%20True%0A%20%20%20%20%22%22%22%0A%20%20%20%20tried_passwords%20%3D%20%5B%5D%0A%20%20%20%20%23Need%20to%20use%20higher%20order%20funtion%0A%20%20%20%20def%20private_account_withdraw%28amount,%20entered_password%29%3A%0A%20%20%20%20%20%20%20%20%23nonlocal%20password%20%23we%20need%20to%20know%20the%20password%20to%20check%20it's%20if%20it%20matches%20only,%20so%20therefore%20we%20don't%20need%20to%20change%20it.%0A%20%20%20%20%20%20%20%20nonlocal%20balance%0A%20%20%20%20%20%20%20%20nonlocal%20tried_passwords%0A%0A%20%20%20%20%20%20%20%20if%20len%28tried_passwords%29%20%3C%203%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20entered_password%20%3D%3D%20password%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20amount%20%3E%20balance%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20'Insufficient%20funds'%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20balance%20%3D%20balance%20-%20amount%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20balance%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20tried_passwords.append%28entered_password%29%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20'Incorrect%20password'%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20%22Frozen%20account.%20Attempts%3A%20%22%20%2B%20str%28tried_passwords%29%0A%0A%20%20%20%20return%20private_account_withdraw%0A%20%20%20%20%0Aw%20%3D%20make_withdraw%28100,%20'hax0r'%29%0Aw%2875,%20'a'%29%0A%0Aw%2810,%20'hax0r'%29%0Aw%2820,%20'n00b'%29%0A%0Aw%2810,%20'hax0r'%29%0Aw%2810,%20'l33t'%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=43&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

Next question [[Q3 Repeated]]