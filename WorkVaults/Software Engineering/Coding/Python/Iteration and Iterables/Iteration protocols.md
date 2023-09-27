Python's iterator protocol boils down to the terms iterable and iterator:

1. An iterable is anything that you can get an *iterator* from using `iter`
2. An iterator is an object that can be passed the `next()` function to get the next value in the sequence.

Along with a few rules that dictate how iterable and iterators work:

1. An iterator is "exhausted" (completed) if calling `next` raises a `StopIteration` exception
2. When you use `iter` on an iterator, you'll get the same iterator back
3. Not all iterators can be exhausted (they can keep giving next values forever if they want)

There are two important concepts that a great deal of Python language behavior is constructed:
- iterable objects
	- Can be passed `iter()` to produce an *iterator*
- iterator objects
	- Can be passed the `next()` function to get the next value in the sequence.

## Stopping Iteration with an exception

- A single end
	- Sequences only have one ending, after all, so reaching it is exceptional
- Infinite sequences
- Finding the end of an infinite sequence would be truly exceptional