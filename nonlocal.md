from [includehelp](https://www.includehelp.com/python/nonlocal-keyword-with-example.aspx)
#### What's is nonlocal
- **nonlocal** is keyword(case-sensitive) in python, it is used when we work with the *nested functions* which is declared in ==outer function==, if we do the same, ==**a variable will be created as local and we will not be able to work with a variable in inner function which is declared in outer function.**==

- In such a case, we can define the variable ( which is declared in outer function) as nonlocal variable in inner function using nonlocal keyword
#### Syntax of nonlocal keyword
`nonlocal varible_name`

##### Example:
``` python
def outerfunc():
	a = 10
	def innerfunc():
		# nonlocal binding
		nonlocal a
		a = 100
		
	#calling inner function
	innerfunc()
	# printing the value of a
	print('a:',a)
	
```
###### output:
`a : 100`

##### Example 2: Define two varibles in outer function and make one variable as nonlocal in inner function.
<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=%23%20python%20code%20to%20demonstrate%20an%20example%20of%20nonlocal%20keyword%0A%0A%23nested%20funcitons%0Adef%20outerfunc%28%29%3A%0A%20%20%20%20a%20%3D%2010%0A%20%20%20%20b%20%3D%2020%0A%20%20%20%20%0A%20%20%20%20def%20innerfunc%28%29%3A%0A%20%20%20%20%20%20%20%20%23nonlocal%20binding%0A%20%20%20%20%20%20%20%20nonlocal%20a%0A%20%20%20%20%20%20%20%20a%20%3D%20100%20%23%20will%20update%0A%20%20%20%20%20%20%20%20b%20%3D%20200%20%23%20will%20not%20update,%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23%20it%20will%20be%20considered%20as%20a%20local%20variable%0A%20%20%20%20%20%20%20%20%23%20calling%20inner%20function%0A%20%20%20%20innerfunc%28%29%0A%20%20%20%20%23%20printing%20the%20values%20of%20a%20and%20b%0A%20%20%20%20print%28'a%3A',%20a%29%0A%20%20%20%20print%28'b%3A',%20b%29%0A%23%20main%20code%0A%23%20calling%20the%20function%20i.e.%20outcome%28%29%0Aouterfunc%28%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=14&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
