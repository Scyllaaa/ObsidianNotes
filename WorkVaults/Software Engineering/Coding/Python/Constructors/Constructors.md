---
alias: constructor
---
Constructors are generally used for instantiating an object. The task of constructors is to initialize(assign values) to the data members of the class when an object of the class is created. In Python the __init__() method is called the constructor and is always called when an object is created.  

**Syntax of constructor declaration :** 
```python 
def __init__(self):
    # body of the constructor
```

**Types of constructors :** 

- **default constructor:** The default constructor is a simple constructor which doesn’t accept any arguments. Its definition has only one argument which is a reference to the instance being constructed.
- **parameterized constructor:** constructor with parameters is known as parameterized constructor. The parameterized constructor takes its first argument as a reference to the instance being constructed known as self and the rest of the arguments are provided by the programmer.
**Example of default constructor :**   
 

```python
class GeekforGeeks:  
	# default constructor
	def __init__(self):  
	self.geek = "GeekforGeeks"` 
	
	# a method for printing data members 
	def print_Geek(self):       
	print(self.geek)`
	
# creating object of the class
obj = GeekforGeeks()

# calling the instance method using the object 
obj.print_Geek()
```

**Output**
```bash
GeekforGeeks
```
[[Advantages of using constructors in Python]]
[[Disadvantages of using constructors in Python]]