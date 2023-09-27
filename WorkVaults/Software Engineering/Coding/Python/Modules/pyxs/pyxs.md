# What is `pyxs`?

It’s a pure Python XenStore client implementation, which covers all of the `libxs` features and adds some nice Pythonic sugar on top. Here’s a shortlist:

- `pyxs` supports both Python 2 and 3,
- works over a Unix socket or XenBus,
- has a clean and well-documented API,
- is writen in easy to understand Python,
- can be used with [gevent](http://www.gevent.org) or [eventlet](http://eventlet.net).

# Installation
If you have [pip](https://pip.pypa.io/en/stable) you can do the usual:
```Bash
pip install --user pyxs
```

Otherwise, download the source from [GitHub](https://github.com/selectel/pyxs) and run:
```Bash
python setup.py install
```
