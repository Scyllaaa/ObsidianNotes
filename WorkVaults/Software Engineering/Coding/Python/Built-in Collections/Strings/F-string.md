### F-string Syntax
```Python
f"one plus one iws {1+1}"
```
- The expressions inside the curly brackets are evaluated and inserted at runtime
```Python
value = 4 * 20
f'The value is {value}'
```
- Because f-strings allow you to use any Python expression, you're not limited to using simple named references. You can, for example, call functions.
```Python
>>> import datetime
>>> f'The current time is {datetime.datetime.now().isoformat}'
'The current time is 2023-10-18T17:42:58.471206'
>>> import math
>>> f'Math constants: pi={math.pi:.3f}, e{math.e:.3f}'
'Math constants: pi=3.142, e=2.718'
```
- If you put an `!r` after the expression, the [[repr()]] representation of the value will be inserted into your string. In the case of exceptions, this gives us more detailed information about the type of exception.
```Python
import sys

DIGIT_MAP = . . .

def convert(s):
	try:
		number = ''
		for token in s:
			number += DIGIT_MAP[token]
		return int(number)
	except (KeyError, TypeError) as e:
		print(f"Conversion error: {e!r}", 
			  file=sys.stderr")
		return -1
```

```Bash
>>> from exceptional impoort convert
>>> convert("fail".split())
Conversion error: KeyError('fail')
-1
```
