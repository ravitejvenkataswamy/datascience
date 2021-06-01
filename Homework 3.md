- [[Tree]]s and [[Data abstraction]]  #done 
    - ![](https://trello-attachments.s3.amazonaws.com/608962b5cfb74007efa57690/609554550a55b1847071f65d/ae65cd8cc61e20d7df1d6de5f5b2c7d2/Screenshot_2021-05-08_at_7.10.32_PM.png)
- [x] Question 1
```shell
superbeliever@Ravitejs-MacBook-Air hw03 % python3 -i hw03.py    
>>> v = mobile(arm(4, t), arm(2, u))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 't' is not defined
>>> t = mobile(arm(1, planet(2)),
...                arm(2, planet(1)))
>>> t
['mobile', ['arm', 1, ['planet', 2]], ['arm', 2, ['planet', 1]]]
>>> total_weight(t)
3
>>> is_mobile(end(left(t))
... )
False
>>> is_mobile(end(right(t)))
False
>>> is_mobile(end(right(t)))
False
>>> total_weight(end(left(t))
... )
2
>>> length(left(t))
1
>>> tf = total_weight(end(left(t))) * length(left(t))
>>> tf
2
>>> rt = total_weight(end(right(t))) * length(right(t))
>>> rt
2
>>> 
```

- [x] Question 2
```python
def totals_tree(m):
    """Return a tree representing the mobile with its total weight at the root.

    >>> t, u, v = examples()
    >>> print_tree(totals_tree(t))
    3
      2
      1
    >>> print_tree(totals_tree(u))
    6
      1
      5
        3
        2
    >>> print_tree(totals_tree(v))
    9
      3
        2
        1
      6
        1
        5
          3
          2
    >>> from construct_check import check
    >>> # checking for abstraction barrier violations by banning indexing
    >>> check(HW_SOURCE_FILE, 'totals_tree', ['Index'])
    True
    """
    "*** YOUR CODE HERE ***"
    #Think about the base case
    #get the total_weight of the mobiles
    #create new tree() with wright at the root. at the label as the convention
    #pass total_weight as the label
    #recursive on the left and right arm to get total_weight of the those as well.

    if is_planet(m):
        return tree(total_weight(m))
    else:
        left_tree, right_tree = totals_tree(end(left(m))), totals_tree(end(right(m)))
        return tree(label(left_tree)+label(right_tree), [left_tree, right_tree])
```
    
	

- finished q3 in less than 10 mins. it's similar to `fib_tree()`
- [x] Question 3
 ```python
if is_leaf(t):
        if t == [find_value]:
            # t[0] = replace_value #must change this one.
            # return t #also this one. just return replace_value
            # print('something')
            return replace_value

            # return replace_value
    else:
        for branch in branches(t):
            replace_leaf(branch, find_value, replace_value)
        return copy_tree(t)
#Modifies the original tree
```

- [x]  Question 4
 ```python
 
if is_leaf(t):
if t == [find_value]:
return tree(label([replace_value]),[replace_leaf(b, find_value, replace_value) for b in branches(t)])
# else:
#     for b in branches(t):
#         replace_leaf(b, find_value, replace_value)
return tree(label(t),[replace_leaf(b, find_value, replace_value) for b in branches(t)])
```

- Doesn't modify the original tree
- Lot of tries required to get this output.
- Need more understanding in tree and recursion.
- This even works without commenting the else: part I think it is redundant
- 50 tries, see terminal output for more.

- [x]  Question 5
```python
def preorder(t):
    """Return a list of the entries in this tree in the order that they
    would be visited by a preorder traversal (see problem description).

    >>> numbers = tree(1, [tree(2), tree(3, [tree(4), tree(5)]), tree(6, [tree(7)])])
    >>> preorder(numbers)
    [1, 2, 3, 4, 5, 6, 7]
    >>> preorder(tree(2, [tree(4, [tree(6)])]))
    [2, 4, 6]
    """
    "*** YOUR CODE HERE ***"

    # What's your base case?
    # Add your current label
    # Recurse down each child, what should we do with the recursive result?
    # return preordering.


    if is_leaf(t):
        return label(t)
    else:
        for b in branches(t):
            flatten_list = lambda irregular_list:[element for item in irregular_list for element in flatten_list(item)] if type(irregular_list) is list else [irregular_list]
            return flatten_list([t[0]] + [preorder(b) for b in branches(t)])
```
  
  - [ ] Used a code from [stackabuse](https://stackabuse.com/python-how-to-flatten-list-of-lists/)
- ### Conclusion
	- [ ] I need deeper understanding in function, as in what do they return and when do they actually return and when do they don't.
	- [ ] Understanding of Lambda functions, 
	- [ ] Converting lambda functions to normal function, 
		converting [[Recursive]] [[lambda]] functions to [[Recursive]] normal function.
	- [ ] [[Recursive]] functions to [[lambda]] functions.
	- This Homework required longest time ever, approximately 13 hours. [[Preorder]] being the most tiring question, given the gravity of that concept I need to work on that.
	- [ ] Also, need to understand [[flattening the lists]]

