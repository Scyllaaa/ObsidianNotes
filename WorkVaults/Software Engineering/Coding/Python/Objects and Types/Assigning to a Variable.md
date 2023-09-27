What actually happens when we assing a value to a [[variable]]?
	e.g.   `x= 100`

- Python creates an [[int]] [[object]] with a value of 1000, an object reference with the name x, and arranges for x to refer to the int 1000 object.

- When we attempt to reassign x = 500 what does NOT happen is the change of the int 1000 object value.
- What actually happens is that python creates a new immutable interger object with the value 500 and redirects the x reference to point to the new object
- There is now no way to access the int 1000 object, and the python garbage collector will reclaim it at some point.

- A core rule to remember is this, the assignment only ever binds objects to names. It never copies an object to a value.

- Python doesn't have variables in the sense of boxes holding a value.
- Python has named references to objects.
## id()

- Returns an integer identifier that is unique and constant for the lifetime of an object
