All three types of collection comprehensions ( [[List and Set Comprehensions]], and [[Dictionary Comprehensions]]) support an optional filtering [[clause]]. This clause allows us to chose which items of the source are evaluated by the expression on the left. To make this interesting, we'll first find a primality testing predicate function. 

```Python
from math import sqrt
def is_prime(x):
	if x < 2:
		return False
	for i in range(2, int(sqrt(x)) + 1):
		if x % i == 0:
			return False
	return True

>>> [ x for x in range(101) if is_prime(x)]
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
```

- There is a strange looking `x for x` construct here because we are not applying any transformation to the filtered values. The expression in  terms of x is simply x itself.
- There's nothing to stop us combining a filtering predicate with a transforming expression. Here's a dictionary comprehension, which maps numbers with exactly three divisors to a tuple of those divisors. `
```Python
>>> prime_square_divisors = {x*x: (1, x, x*x) for x in range(20) if is_prime(x)}
>>> pp(prime_square_divisors)
{4: (1, 2, 4),
 9: (1, 3, 9),
 25: (1, 5, 25),
 49: (1, 7, 49),
 121: (1, 11, 121),
 169: (1, 13, 169),
 289: (1, 17, 289),
 361: (1, 19, 361)}
```