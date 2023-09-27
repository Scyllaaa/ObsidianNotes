- **Unordered** collection of unique elements.
	- They are iterable, but the order is arbitrary
- Sets are mutable, so far as elements could be added and removed from the set.
- Elements in a set must be immutable.
- The [[set()]] constructor can create a set from any iterable series, such as a list, and duplicates are discarded
- Membership can be determined with the [[in and not in operators]]. 


- To add a single element to a set, use the `set.add()` method. 
	- Adding an element that already exists has no effect, neither does it produce an error.
- Multiple elements could be added in one go from any iterable series including another set using the `set.update()` method.


### Removing an item from a set

There are two methods for removing an item from a set.

- The first, `set.remove()`, requires that the element to be present in the set. Otherwise a key error is produced.
- The second, `set.discard()` is less fussy and simply has no effect if the element is not a member of the set.

## Copying a set
- `set` supports a `set.copy()` method which preforms a [[Shallow Copies|shallow copy]], copying references but not objects.

## Set Algebra

- There are a number of set algebra operations that allow one to easily compute set unions, set differences, and set intersections. 
- They also allow evaluations of whether two sets have subset, superset, or disjoint relations.