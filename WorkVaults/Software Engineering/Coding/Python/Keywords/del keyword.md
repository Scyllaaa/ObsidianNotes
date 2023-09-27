---
alias: del
---
The `del` keyword is used to delete objects. In Python everything is an object, so the `del` keyword can also be used to delete variables, lists, or parts of a list etc.

###### Delete element of a list
```Python
>>> x = ["apple", "banana", "cherry"]  
>>> del x[0]  
>>> x 
["banana", "cherry"]  
```
###### Delete an element from a dictionary
```Python
>>> z = {'H': 1, 'Tc': 43, 'Xe': 54,}
>>> del z['H']
>>> z
{'Tc': 43, 'Xe': 54,}
```