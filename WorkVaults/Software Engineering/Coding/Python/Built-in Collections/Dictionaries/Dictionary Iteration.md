- Dictionaries yield the next key on each iteration
- Values can be retrieved using the square-bracket operator.
#### Iterating over values and keys
- If we want to iterator over only the values, we can use `dict.values()` dictionary method.
	- This returns on object which provides an iterable view onto the dictionary values without causing the values to be copied.
- There is no efficient or convenient way to retrieve the corresponding key from a value, so we only print the values.
- There is also the `dict.keys()` method, providing a symmetrical iterable onto the dictionary keys.

##### dict.items() method
- Each key-pair value in a dictionary is called an item, and to iterate over the keys and values in tandem one can use the `dict.items()` method.
- When iterated, the items view yields each key-pair as a tuple. 
	- By using [[Tuple unpacking]] in a [[For-loops|for-loop]] we can get both the key and value in one operation without the extra loopup.
