
`~` is the [bitwise complement operator](http://en.wikipedia.org/wiki/Bitwise_operation#NOT) in python which essentially calculates `-x - 1`.

It is a unary operator (taking a single argument) that is borrowed from C, where all data types are just different ways of interpreting bytes. It is the "invert" or "complement" operation, in which all the bits of the input data are reversed.

In Python, for integers, the bits of the [twos-complement representation](http://en.wikipedia.org/wiki/Two%27s_complement) of the integer are reversed (as in `b <- b XOR 1` for each individual bit), and the result interpreted again as a twos-complement integer. So for integers, `~x` is equivalent to `(-x) - 1`.

The reified form of the `~` operator is provided as `operator.invert`. To support this operator in your own class, give it an `__invert__(self)` method.

```python
>>> import operator
>>> class Foo:
...   def __invert__(self):
...     print 'invert'
...
>>> x = Foo()
>>> operator.invert(x)
invert
>>> ~x
invert
```

Any class in which it is meaningful to have a "complement" or "inverse" of an instance that is also an instance of the same class is a possible candidate for the invert operator. However, operator overloading can lead to confusion if misused, so be sure that it really makes sense to do so before supplying an `__invert__` method to your class. (Note that byte-strings [ex: `'\xff'`] do not support this operator, even though it is meaningful to invert all the bits of a byte-string.)