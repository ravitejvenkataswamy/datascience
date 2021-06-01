---
date updated: '2021-05-31T23:38:23+05:30'

---

Question 3: **Repeated** [[Iterators]] and [[generators]]
#inprogress #unsolved
Previous quesiton: [[Q2 Password Protected Account]]
![[Homework 4#^a4674d]]

[[2021-05-31]]

#### Problem Description

- Implement a function (not a generator function) that returns the first value in the iterator `t` that appears `k` times in a row.
- As described in lecture, [[Iterators]] can provide values using ewither the [[next]](t) function or with a for-loop.
- Do ==not== worry about cases where ==the function reaches the end of iterator without finding a suitable value==, all lists passed in for the tests will have a value that should be returned.
- If you are receiving an **error** where the iterator has completed then the program is ==not== identifying the **correct value**.
- Iterate through the items such that _if the same [[iterator]] is passed in to `repeated` twice, it continues in the second call at the point it left off in the first._
- ==Return the first value in iterator T that appears K times in a row.==
- Iterate through the items such that if the same iterator is passed into repeated twice, it continues in the second call at the point it left off in the first.

`s = iter([10, 9, 10, 9, 9, 10, 8, 8, 8, 7])`
`repeated(s, 2)`
`8`

### _Hints_:

Using for loop for iteration might help here
`for i in ri:
		print(i)`

`for` loops will iterate over iterators themselves

[[map]]s can used. We kind of need to lazy programming, I guess.
[[filter]]s seem more relavent here than [[map]], altough map and filter work together, let's see how we can implement this question

Write a function that checks current and next term same

```python
def functions()
```


# Stuck here from 2 day