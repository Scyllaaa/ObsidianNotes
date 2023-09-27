```Python
while True:
    try:
        x = int(input("Please enter a number: "))
        break
    except ValueError:
        print("Oops!  That was no valid number.  Try again...")
```

The [`try`](https://docs.python.org/3/reference/compound_stmts.html#try) statement works as follows.

- First, the _try clause_ (the statement(s) between the [`try`](https://docs.python.org/3/reference/compound_stmts.html#try) and [`except`](https://docs.python.org/3/reference/compound_stmts.html#except) keywords) is executed.
- If no exception occurs, the _except clause_ is skipped and execution of the [`try`](https://docs.python.org/3/reference/compound_stmts.html#try) statement is finished.
- If an exception occurs during execution of the [`try`](https://docs.python.org/3/reference/compound_stmts.html#try) clause, the rest of the clause is skipped. Then, if its type matches the exception named after the [`except`](https://docs.python.org/3/reference/compound_stmts.html#except) keyword, the _except clause_ is executed, and then execution continues after the try/except block.
- If an exception occurs which does not match the exception named in the _except clause_, it is passed on to outer [`try`](https://docs.python.org/3/reference/compound_stmts.html#try) statements; if no handler is found, it is an _unhandled exception_ and execution stops with a message as shown above.