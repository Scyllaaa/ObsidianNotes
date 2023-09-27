- Index from the end of sequences using negative numbers.
- The last element is at index -1.

```python
>>> r = [ 1, -4, 10]
>>> r[-1]
10
>>> r[-2]
-4
>>> r[0]
1
>>> r[-0]
1
```

- Since there is no difference between index 0 and index -0, negative indexing is essentially 1-based rather than 0-based