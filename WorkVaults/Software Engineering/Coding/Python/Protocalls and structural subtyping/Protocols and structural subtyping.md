- A set of operations or methods that a type must support to implement the protocol.
- Do not need to be defined in the source code as separate interfaces or base ( as they would in nominally typing languages such as [[C++]] or [[Java]])
- Types only need to provide functioning implementations of those operations.



The Python type system supports two ways of deciding whether two objects are compatible as types: nominal subtyping and structural subtyping.

_Nominal_ subtyping is strictly based on the class hierarchy. If class `Dog` inherits class `Animal`, it’s a subtype of `Animal`. Instances of `Dog` can be used when `Animal` instances are expected. This form of subtyping subtyping is what Python’s type system predominantly uses: it’s easy to understand and produces clear and concise error messages, and matches how the native [`isinstance`](https://docs.python.org/3/library/functions.html#isinstance "(in Python v3.11)") check works – based on class hierarchy.

_Structural_ subtyping is based on the operations that can be performed with an object. Class `Dog` is a structural subtype of class `Animal` if the former has all attributes and methods of the latter, and with compatible types.

Structural subtyping can be seen as a static equivalent of duck typing, which is well known to Python programmers. See [**PEP 544**](https://peps.python.org/pep-0544/) for the detailed specification of protocols and structural subtyping in Python.

- [[Predefined protcols]] 
- [[Simple user-defined protocols]]