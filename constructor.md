---
date updated: '2021-05-29T15:12:33+05:30'

---

- allocate memory for a `Ball` object
- initialises the `Ball` object with values
- returns address of the Ball objects
- similar to a `list`
  - [    ] slightly different syntax for calling in the  [[constructor]]
  - Bunch of data elements in the list
  - What does python do:
    - allocate memory for a `Ball` object, well in this case it's a `list`
    - initialises the `Ball` object with values, with list name, sticks the data in there
    - returns address of the Ball objects, well `list` object
- ==The constructor must must must must must have the following name you have no choice in this== `__init__`
- If you don't have a constructor you don't have an object to instantiate, it just a waste of time
- ==What's==  [[self]]
  - The memory allocation is done **beyond the scenes** as soon as the [[self]] is called
  - The [[self]] is the [[Object]]
  - The `__init__` must must have the first argument `self`
    - `self` is used because the python will store the address of the `object` of that particular `class` that python created for you
