zip
```python
    >>> d = {'a': 1, 'b': 2}
    >>> d
    {'b':2, 'a': 1}
    >>> items1 = iter(d.items())
    >>> next(items1)
    ('b', 2)
    >>> next(items1)
    ('a', 1)
    #Order is consistent

    Another way to get us to zip them
    >>> items1 = zip(d.keys(), d.values())
    >>> next(items)
    ('b', 2)
    >>> next(items1)
    ('a', 1)
    #Again the order is consistent and reliable.
```