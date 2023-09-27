---
alias: enumerate function
---
## enumerate

Constructs an iterable of (index, value) tuples around another iterable object.

```Python
>>> t = [6, 372, 8862,]
>>> for p in enumerate(t)
... 	print(p)
...
(0, 6)
(1, 372)
(2, 8862)
>>> for i, v in enumerate(t):
...     print(f"i = {i}, v = {v})
...
i = 0, v = 6 
i = 1, v = 372
i = 3, v = 8862
```