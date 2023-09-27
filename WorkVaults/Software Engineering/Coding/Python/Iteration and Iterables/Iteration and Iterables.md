- An [[iterable]] is an object from which you can fetch a sequence of other objects.
- The act of fetching a sequence from an iterable is known as an [[iteration]]
- Comprehensions expressions can be arbitrarily complex
- Avoid [[Complex Expressions]] - Extract complex expression into separate functions to preserve readability.

- [[List and Set Comprehensions]]
- [[Dictionary Comprehensions]]
- [[Filtering Comprehensions]]
- [[Iteration protocols]]
- [[Generator Functions]]
- [[Maintaining State in Generators]]
- [[Laziness and the Infinite]]
- [[Generator Expressions]]
- [[Iteration Tools]]

## Section Summary
- Use [[iter()]] to get an iterator from an iterable object.
- Use [[next()]] to get the next item from an iterable. 
- Iterator raise [[StopIteration Exception]] when they're exhausted
- [[Generator Functions]] contain at least once [[yield keyword]]
- Generators themselves are iterators
- Each call to a generator function produces a new generator
- Generators maintain explicit internal state
- Generators yield values lazily
- [[Generator Expressions]] are a type of comprehension that creates generators. 
- Built-in iteration tools include [[sum()]], [[any()]], and [[zip()]].
- The [[itertools]] modules includes many other tools for iteration