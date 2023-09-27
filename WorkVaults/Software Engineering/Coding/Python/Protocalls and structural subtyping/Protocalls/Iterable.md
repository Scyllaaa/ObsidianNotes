The [`typing`](https://docs.python.org/3/library/typing.html#module-typing "(in Python v3.11)") module defines various protocol classes that correspond to common Python protocols, such as [`Iterable[T]`](https://docs.python.org/3/library/typing.html#typing.Iterable "(in Python v3.11)"). If a class defines a suitable [`__iter__`](https://docs.python.org/3/reference/datamodel.html#object.__iter__ "(in Python v3.11)") method, mypy understands that it implements the iterable protocol and is compatible with [`Iterable[T]`](https://docs.python.org/3/library/typing.html#typing.Iterable "(in Python v3.11)"). For example, `IntList` below is iterable, over `int` values:
```Python
class IntList:
    def __init__(self, value: int, next: Optional['IntList']) -> None:
        self.value = value
        self.next = next

    def __iter__(self) -> Iterator[int]:
        current = self
        while current:
            yield current.value
            current = current.next

def print_numbered(items: Iterable[int]) -> None:
    for n, x in enumerate(items):
        print(n + 1, x)

x = IntList(3, IntList(5, None))
print_numbered(x)  # OK
print_numbered([4, 5])  # Also OK
```

The [example above](https://mypy.readthedocs.io/en/stable/protocols.html#predefined-protocols) has a simple implementation of an [`__iter__`](https://docs.python.org/3/reference/datamodel.html#object.__iter__ "(in Python v3.11)") method.
```Python
def __iter__(self) -> Iterator[T]
```
