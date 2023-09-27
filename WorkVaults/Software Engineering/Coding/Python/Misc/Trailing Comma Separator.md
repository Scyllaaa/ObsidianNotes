When you are defining a data structure in Python, like a [[Software Engineering/Coding/Python/Datatypes/Dictionaries|dictionary]], a [[Tuples|tuple]], a [[Software Engineering/Coding/Python/Built-in Collections/Lists/Lists|list]], etc.:

```
capitals = {
    'China': 'Beijing',
    'India': 'New Delhi',
    'Mexico': 'Mexico City',
}
```

You can leave a trailing comma on the last entry. It is useful because then every line has the same format and adding entries to the end is the same as adding them to the middle.

It also prevents the frequent bug of writing:

```Python
countries = [
    'China',
    'India'
]
```

And then later adding 'Mexico':

```Python
countries = [
    'China',
    'India'
    'Mexico'
]
```

Which creates the list:

```Python
['China', 'IndiaMexico']
```