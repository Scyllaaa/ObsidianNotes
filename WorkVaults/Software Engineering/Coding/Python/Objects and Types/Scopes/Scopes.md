- Type declarations are unnecessary in Python.
- Names can be rebound as necessary to object of any type.
- Name resolution to object is managed by scopes and scoping rules. 

Each scope is a context in which names are stores and can be looked up.
From narrowest to broadest are:

- Local - Inside the current function
- Enclosing - Inside enclosing functions
- Global - At the top level of the module
- Built-in - In the special `builtins` module

- Scopes in Python do not correspond to source code blocks as demarcated by indentation. For loops and the like do not introduce new nested scopes.

Sometimes we will need to [[Rebinding Global Names|rebind global name]], that is, one defined at a module scope, from within a function. 