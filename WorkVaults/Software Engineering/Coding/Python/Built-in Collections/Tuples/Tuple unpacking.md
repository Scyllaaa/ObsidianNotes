De-structuring operation that unpacks data structures into named references.

For example 
```python
lower, upper = minmax([83,82.85])
```


You can also swap using unpacking e.g:

```
>>> a = 'jelly'
>>> b = 'bean'
>>> a, b = b, a
>>> a
'bean'
>>> b
'jelly'
```

- You can also create a tuple from an existing collection object by using the `tuple` [[Constructors|constructor]]
- You can also do this with a string, or in fact any type over which you can iterate.
- We can test for containment for containment with the `in` operator, and 