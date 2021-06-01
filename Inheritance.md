---
date updated: '2021-06-02T00:38:52+05:30'

---

#inprogress
lecture 19

- When it is applied appropriately, this can be of greater use, not otherwise. Often overused
- Recall [[attribute]]: Recalled from [[Inheritance]] perspective

```qrcode
Inheritance
```

[Lecture playlist](https://www.youtube.com/watch?v=m9wC1N9PtSw&list=PL6BsET-8jgYXpV7vl4Pvo25wh0FKRlecx)

[[ANTS]]: Ants Vs. SomeBees

### [[attribute]]

^d70870

- - Recalled from [[Inheritance]] perspective
  - Terminology: [[attribute]]s, [[function]]s, and [[method]]s
    - All [[object]]s have attributes, which are name-value pairs
    - [[class]]es are objects too, so they have attributes
    - Instance attribute: attribute of an intsance
    - Class attribute: attribute of the class of an instance

![[Drawing 2021-06-01 23.56.20.excalidraw]]

- Functions aren't particular to [[Object-Oriented Programming]], but [[method]] are.
  - Method is function that's also a class attribure ^2072af

##### ==Python object system==

1. Functions are objects
2. [[bound method]]s are also objects: a function that has its first paremeter [[self]] already bound to an instance.
3. [[dot expression]]s evalute to bound methods for class attributes that are functions

`<instance>.<method_name>` is a very common pattren
where you put some <instance> here before the (dot) and after the dot you have a method name; then that method is function named with the instance filled in as self parameter

A quick review on how [[dot expression]]s work

```shell
	<instance>.<method_name>
```

#### To evaluate a [[dot expression]]

- Evaluate the `<expression>`  to the left of the dot, which yields the [[Object]] of the [[dot expression]]

- `<name>`  is matches against the instance attributes of that object;
  if an attribute with the name exists, its value is returned(value in the sense value of the whole [[dot expression]])

- If not, <name> is looked up in the class, which yields a [[class]] attribute value.

- That [[attribute]] value is returned unless it is a function, in which case a [[bound method]] is returned instead.
  a slighly different version of function, where you get the function, with it's first parameter bound already to the object of the [[dot expression]]
