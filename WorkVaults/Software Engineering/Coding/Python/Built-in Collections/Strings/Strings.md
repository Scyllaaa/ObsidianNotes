- Concatenation of strings is supported with the `+` operator 
- Strings are immutable. You can not modify them in place
- `str.join()` is a more efficient method for joining many strings.

1. Concatenation with `+` results in temporaries with consequent costs for memory, allocations and copies
2. `str.join()`` inserts a separator between a collection of strings.
3. Call `join()`` on the separator string

## Moment of Zen

- The way may not be obvious at first 
	- To concatenate Invoke join on empty text 
	- Something form nothing

- Another useful method is the `.partition` method which is often used in alongside [[Tuples]]. 
- There is a convention in python that the `_` character is used to denote unused or dummy values.
-
### String formatting

The `.format` method can be called on any string that contains *replacement fields* denoted by curly brackets {}. The objects provided as arguments are converted to string and used to populate these fields. 

- The objects can address using index numbers in the replacement fields.
- The same object can be referenced multiple times in the same string.
- If each object is omitted only once in the matching order that they appear in the string, the index numbers can be omitted. 
- Alternatively keyword arguments can be used to address the object arguments. 
- It is possible to index into sequences using square brackets inside the replacement fields.
- You can also address modules attributes, as modules are also objects
- Format strings also give us a lot of control over field alignment and floating point formatting. e.g
``` PYTHON
import math
	"Math constants: pi={m.pi:.3f}, e={m.e:.3f}".format(m=math)
```

### PEP 498: Literal String Interpolation
- Commonly called [[F-string]]s
- "Embed expressions inside literal strings, using minimal syntax"