- Iterables defined by functions
	- Python generators provide the means for describing iterable series with code in functions
- Lazy evaluation
	- These sequences are evaluated lazily, meaning they only compute the next value on demand.
- Can model sequences with no definite end
	- e.g. streams of data from a sensor or active log files.
- Composable into pipelines
	- With careful design, we can make generic stream processing elements, which can be composed into sophisticated pipelines.

Generators are defined by any Python function which uses the [[yield keyword]] at least once in its definition.
They may also include the [[return keyword]] with no arguments 

- Because generators are iterators and because iterators must also be iterable, they can also be used in all the usual; Python constructs which expect iterable objects, such as [[For-loops|for-loop]]s
- Each call to a generator function returns a new generator object.