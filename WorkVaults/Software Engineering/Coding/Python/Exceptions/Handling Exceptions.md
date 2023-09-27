It is possible to write programs that handle selected exceptions. Look at the following example, which asks the user for input until a valid integer has been entered, but allows the user to interrupt the program (using Control-C or whatever the operating system supports); note that a user-generated interruption is signalled by raising the [`KeyboardInterrupt`](https://docs.python.org/3/library/exceptions.html#KeyboardInterrupt "KeyboardInterrupt") exception.
```Python
while True:
    try:
        x = int(input("Please enter a number: "))
        break
    except ValueError:
        print("Oops!  That was no valid number.  Try again...")
```

A [[try statement]] may have more than one _except clause_, to specify handlers for different exceptions. At most one handler will be executed. Handlers only handle exceptions that occur in the corresponding _try clause_, not in other handlers of the same `try` statement. An _except clause_ may name multiple exceptions as a parenthesized tuple, for example
