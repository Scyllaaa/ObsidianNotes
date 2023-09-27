Generator expressions are a cross between comprehensions and [[Generator Functions]]
They use a similar syntax as comprehensions, but they result in the creation of a generator object, which produces the specified sequence lazily. 

## Generator Expressions syntax
```Python
(expr(item) for item in iterable)
```

- Useful for situation where you want the lazy evaluation of generators with the declarative concision of comprehensions.
- A generator object is just an iterator, and once run exhaustively, will yield no more items.
- Generators are single use object
```Python
>>> million_squares = (x*x for x in range(1, 1000001))
>>> million_squares
<generator object <genexpr> at 0x7feb7c914f20>
>>> list(million_squares)[-10:]
[999982000081, 999984000064, 999986000049, 999988000036, 999990000025, 999992000016, 999994000009, 999996000004, 999998000001, 1000000000000]
>>> list(million_squares)
[]
```
- Each time we call a generator we create a new generator object.
- To recreate a generator from a generator expression, one must execute the expression itself once more.

- One could also include an `if` [[clause]] in the end of the generator expression. 
### Optional Parentheses
- Python generator expressions have the elegant ability to have the parenthesis used for the function call also server for the generator expression aids readability.
```Python
func ( expr(item) for item in terable )
     ^-----One set of parenthesis-----^
# However, the following would still be allowed
func( ( expr(item) for item in terable ) )
```