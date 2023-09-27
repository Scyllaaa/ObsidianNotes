Variables can be created in a few ways, and they can be initialized or not. If a variable is not initialized, it takes the type's zero value. Let's use the [[var keyword]] to declare one or many variables. This can be done on the package or function level:
```go
var (
	index int //int zero-value is 0
	noWord string //string zero-value is ""
	didWeLearnSomething bool = true //bool zero-value is false, but we're initializing the variable with true instead
)
```

Let's use the short variable declaration. This can only be done inside a function:
```go
index := 3 //short variable declaration infers the type. In this case, index will be an int
noWord := ""
someWord := "bird"
```