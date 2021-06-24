---
creation date: 2021-06-24 11:04


---
[[2021-06-24]]

### range

```python
square, odd = lambda x: x * x, lambda x: x % 2 == 1
list(map(square, filter(odd, range(1, 6)))) #[1, 9 ,25]
```