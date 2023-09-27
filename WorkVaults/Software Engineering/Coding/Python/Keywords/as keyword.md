The `as` keyword is used to create an alias. 
In the example below, we create an alias, `c`, when importing the calendar module, and now we can refer to the calendar module by using `c` instead of `calendar`.

```Python
>>> import calendar as c   
>>> print(c.month_name[1])
January
```