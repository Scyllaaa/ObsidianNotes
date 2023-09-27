Exception handling is a mechanism for interrupting normal program flow and continuing in surrounding context or code block

### Exceptions: Key Concepts

1. Raising an exception
	1. The event of interrupting normal flow is called the act of raising an exception. 
2. Handling an exception
	1. In some enclosing context, the raised exceptions must be handled upon which control flow is transferred to the exception handler.
3. Unhandled exception
	1. If the exception propagates up the [[callstack]] to the start of the program, then an unhandled exception will cause the program to terminate.
4. Exception objects
	1. An exception object containing information about where and why an exceptional event occurred is transported from the point at which the exception was raised to the exception handler so that the handler can interrogate the exception object and take appropriate action.

The python philosophy is at the liberal end of the spectrum when it comes to the use of exceptions.

- Empty code blocks are not permitted in Python programs

### Programmer Errors
Exceptions resulting from programmer errors:
- [[IndentationError]]
- [[SyntaxError]]
- [[NameError]]
These should almost never be caught.
The fact that these things are exceptions is mostly useful if you're creating a Python development tool, such as a Python IDE, embedding Python itself in a larger system to support application scripting, or designing a plugin system which dynamically loads code.


## Use Standard Exceptions Types

- Standard types
	- Python provides standard exception types for signaling common errors
- Invalid argument values
	- Use [[ValueError]] for arguments of the right type but with an invalid value
- Exception constructors
	- Use [[raise keyword|raise]] [[ValueError()]] to raise a new ValueError

### Avoid Explicit Type Checks

- We tend not to protect against type errors in Python as this would run against the grain of dynamic typing in Python and limits the reuse potential of code we write.
- Usually in Python it is not worth adding type checking (catching `TypeError`) to functions.
- If a function works with a particular type, even one that you couldn't have known about when you designed the function, then that's all good. - Increased function reusability.
	- If not, execution will probably result in a `TypeError` anyway.

### It's Easier to Ask Forgiveness Than Permission
There are only two approaches to dealing with a program operation that might fail:

1. Check all precondition
2. Prepare for consequences
In python culture, these two philosophies are known as 

- LBYL- Look Before You Leap
- EAFP - Easier to ask forgiveness than permission (note: a term coined by rear admiral Grace Hopper, inventor of the compiler)

Python strongly prefers EAFP because it puts primary logic for the happy path in its most readable form with deviations from the normal flow handled separately rather than interspersed with the main flow.
- EAFP is **enabled** by exceptions 
	- EAFP is standard in Python, and that philosophy is enabled  by exceptions.
- Without exceptions, error handling is **interspersed** in program flow
	- Without exceptions, that is, using error codes instead, one is forced to include error handling directly in the main flow of program logic.
- Exceptions can be handled **non-locally**
	- Since exceptions interrupt the main flow, they allow you to handle the exceptional cases non-locally.

Exceptions coupled with EAFP are also superior because: 
1. Exceptions are **not easily ignored**
2. Error codes are **silent by default**
3. Exceptions plus EAFP makes it **hard for problems to be silently ignored** 

### Cleanup actions
- Sometimes you need to perform a cleanup action, irrespective of whether an operation succeeds.
- [[Context Managers]] are the modern solution to this common situation.
- [[try-finally construct]] - The finally-block always executed regardless of how they [[try statement]] block exits.