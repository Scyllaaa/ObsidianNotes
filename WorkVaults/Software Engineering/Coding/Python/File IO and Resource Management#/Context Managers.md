### Creating a Simple Context Manager

Use `closing` from `contextlib` module

Wrap a custom constructor call in a call to closing which will wrap the object in a context manager that always calls the close method on the wrapped object before exiting.