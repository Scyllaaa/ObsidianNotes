Here is an example of the most complex from of expressions one should use for comprehension

```Python
>>> import os
>>> import glob
>>> file_sizes = {os.path.readpath(p): os.stat(p).st_size for p in glob.glob('*.py*')}
>>> pp(filze_sizes)
{'/core-python/script.py' : 649
 '/core-python/session.py': 283}
```
