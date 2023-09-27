Extended form of indexing for referring to a portion of a list or other sequence

Syntax: `a_list[start:stop`]

```Python
>>> s = [3, 186, 4431, 74400, 1048443]
>>> s[1,3]
[186, 4431]
>>> s[1:-1]
[186, 4431. 74400]
```

- Both the start and stop indexes are optional

```Python
>>>s[2:]
[4431, 74400, 1048443]
>>> s[:2]
[3, 186]
```

- Notice that these two lists together form the whole list, demonstrating the convenience of the half open range convention.

- Since both the `start` and `stop` indexes are optional, it is possible to omit them and return the whole list.

```Python
>>> s[:]
[3, 186, 4431, 74400, 1048443]
```

- This last example is an important idiom for copying a list. 
- Recall that assigning references never copies an object, but merely copies a reference to an object. 

```Python
>>> t = s
>>> t is s
True
```

- We deploy the full slice to preform a copy into a new list. 
- This gives a new object with a distinct identity, but since its a copy, the new object has an equivalent value.
```Python
>>> r = s[:]
>>> r is s
False
>>> r == s
True
```

- It's important to understand that although we have a new list object, which can be independently modified, the elements within it are references to the same objects referred to by the original list.
- In the event that these objects are both mutable and modified, as opposed to replaced, the change will be seen in both lists.


- There are more readable ways of copying a list, such as the `copy` method, or by passing the list to the `list()` constructor.
- The `list()` method is preferred as it has the advantage of working with any iterable series as the source, not just lists.
```Python
>>> u = s.copy()
>>> u is s
False
>>> v = list(s)
```

- All of these techniques preform [[Shallow Copies]], that is, they create a new list containing the same object references as the source list, but they don't copy the referred-to objects.