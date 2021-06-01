---
date updated: '2021-05-31T21:47:09+05:30'

---
### iterator
Passing a list to a [[iter]] function creates an [[list_iterator]] object
Passing a dictionary to a [[iter]] function creates an [[dict_keyiterator]] object  **by default**
Passing a `d.keys()` to a [[iter]] function creates an ` dict_keyiterator object  `
Passing a `d.items()` to a [[iter]] function creates an ` dict_itemiterator object  `
Passing a `d.keys()` to a [[iter]] function creates an ` dict_keyiterator object  `
Passing a 'range(0, n)' to a [[Iter]] function creates an `range_iterator object`

Where d is `  { 'a':2,'b':4} `

    >>> s = iter([1,2,3,4])
    >>> s
    <list_iterator object at 0x1052fa130>
    >>>

Only way to access the elements using this [[iter]] function is to use [[next]] function?

passing a list iterator object to next will return the value of currently pointing value and mutate the list iterator object to point to next value
