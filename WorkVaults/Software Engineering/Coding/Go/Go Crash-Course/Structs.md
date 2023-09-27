A struct is a collection of fields (private or public).

```go
type Person struct {
	ID int
	Name string
	Phone string
}
```

Structs can be "instantiated" using literals, like this:

```go
person := Person{
	ID:    1,
	Name:  "Cool Person",
	Phone: "+1 111 1111-1111",
}

fmt.Println(person.Name) //struct fields can be accessed through the dot syntax
```

