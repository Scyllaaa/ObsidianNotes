---
alias: dictionary, dictionaries
---
## Creating a dictionary
- Literal dictionaries are delimited by curly braces and contained comma-separated key-value pairs, with each pair tied together by a colon. 
	- There is also the [[dict()]] constructor, which can convert other types to dictionaries.
- Internally, the dictionary maintains pairs of  references to the key object and the value objects.
	-  Do not rely on the order of the items in the dictionary, as it is essentially random and may even vary between runs of the same program.
- These values are accessible via the keys.
	- The key objects must be immutable, so [[Software Engineering/Coding/Python/Built-in Collections/Strings/Strings|Strings]], numbers, and [[Tuples|tuple]]s are fine, but [[Software Engineering/Coding/Python/Built-in Collections/Lists/Lists|lists]] are not. 
- Since each key is associated with exactly one value, and lookup is through keys, the keys must be unique within any single dictionary. It's fine however to have duplicate values.
	- The value object can be mutable.
- The dictionary itself is mutable.
## Dictionary Copying
- As with [[Software Engineering/Coding/Python/Built-in Collections/Lists/Lists|lists]], [[Dictionary Copying]] is shallow by default, copying only the references to the key and value object, not the objects themselves.
## Updating a dictionary
- If you need to extend the dictionary with definitions from another dictionary, you can use the `dict.update()` method.
	- Call this upon the dictionary that is to be updated and is passed the contents of the dictionary which is to be merged in.
	- If the argument update incudes keys which are already present in the target dictionary, the values associated with these keys are replaced in the target by the corresponding values from the source.
## Misc

- [[Dictionary Iteration]]

- Can use the [[in and not in operators]] to test membership on the keys of a dictionary.

- Can use the [[del keyword]] to remove and entry from a dictionary.  

	- To get a more readable form, one can use the pretty-printing standard python module called [[pprint module]], which contains a function called `pprint`.