Pointers hold addresses to values. This is called "referencing a value". The zero value of a pointer is `nil`.

```go
var index *int
fmt.Println(index)  //the zero value for pointers is nil, so that's what will be printed out
i := 4              //we assign 4 to variable i
index = &i          //the & token grabs the address of a variable, in this case we're assigning the address of i to index
fmt.Println(index)  //this will print out the memory address
fmt.Println(&i)     //checking that's the same address of i
fmt.Println(*index) //the * token is used for both declaring a pointer and for dereferencing a variable, getting its value
i = 42              //this will change index's value as well, since they point to the same memory address
fmt.Println(*index) //checking that index now holds 42
```
