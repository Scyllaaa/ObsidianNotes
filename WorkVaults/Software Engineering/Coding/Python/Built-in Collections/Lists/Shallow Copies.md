---
alias: shallow copy
---
To shallow copy is to create a new list containing the same object references as the source list, but they don't copy the referred-to objects.

- To demonstrate this, we can look at nested lists with the inner lists serving as mutable objects.

```Python
>>> a = [ [1, 2], [3, 4] ]
>>> b = a[:]
False
>>> a == b
True
```

- After copying this list using a full slice, we confirm that we do indeed have distinct lists with equivalent values. 
- Notice however that the references within these distinct lists refer not only to equivalent objects, but, in fact, to the same object which we can see is using the is operator.
```Python
>>> a[0]
[1, 2]
>>> b[0]
[1, 2]
>>> a[0] is b[0]
True
```

- The first elements of `a` and `b` are the same object until we rebind the first element of a to a newly constructed list. 
- Now the first elements of lists `a` and `b` refer to different lists with different values
```Python 
>>> a[0] = [8, 9]
>>> a[0]
[8, 9]
>>> b[0]
[1, 2]
```

- The second element's of both `a` and `b` still refer to the same object. 
- We can demonstrate this by mutating that object through the `a` list, which we can see this change reflected through the `b` list.

```Python
>>> a[1].append(5)
>>> a[1]
[3, 4, 5]
>>> b[1]
[3, 4, 5]
>>> a
[[9, 9], [3, 4, 5]]
>>> b
[[1, 2], [3, 4, 5]]
```

- If one needs to preform true deep copies of hierarchical data structures like this, it is recommended to delve into the `copy` module in the Python standard library.