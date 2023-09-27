---
alias: list, lists
---
- [[Negative indecies]]
- [[Shallow Copies]]
- [[Slicing]]
- [[Removing an item from a list]]
- [[Inserting an item into a list]]
- As with [[Software Engineering/Coding/Python/Datatypes/Strings|Strings]] and [[Tuples]], lists support repetition using the multiplication operator `*`.
- It is most often used to initialize a list with a known size in advance with a constant value, such as 0.
```Python
>>> c = [21, 37]
>>> d = c *4
>>> d 
[21, 37, 21, 37, 21, 37, 21, 37]
>>> [0] * 9
[0, 0, 0, 0, 0, 0, 0, 0, 0]
```
- When using mutable objects as elements, repetition will repeat the reference without copying the value.
- We can demonstrate this using lists as mutable elements
```Python
>>> s = [ [-1, +1] ] * 5
>>> s
[[-1, +1], [-1, +1], [-1, +1], [-1, +1], [-1, +1]]
>>> s[2].append(7)
>>> s
[[-1, 1, 7], [-1, 1, 7], [-1, 1, 7], [-1, 1, 7], [-1, 1, 7]]
```
- This happens because each element of the outer list is a reference to the same nested list object.

- The `list.count()` method returns the number of times the specified element appears in the list.
- Use the `list.index()` method to find the location of an object in a list
- This returns the index of the first list element which is equal to the argument. 

- To test for membership (i.e. does the list contain the value x) you can use the `in` operator, or you can test for non-membership with `not in`.

- Concatenating lists using the [[addition operator]] `+` results in new lists without modification of the operands, whereas the [[Augmented Assignment Operators|augmented assignment operator]] `+=` , modified the assignee in place.
- This can also be achieved using the `list.extend()` method.
- All of these techniques work with any iterable series on the right-hand side.

[[Reversing and Sorting Lists]]
