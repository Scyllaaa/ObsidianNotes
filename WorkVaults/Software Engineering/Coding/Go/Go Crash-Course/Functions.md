A function can take zero or more arguments. It can return zero or more values as well. When a function fails for some reason, it's considered good practice to return a result _and_ an error. Function callers can then check if the error is nil to understand if everything went as expected.

Named functions need to be declared outside of other functions, while anonymous functions can be declared inside functions.

```Go
package main

import (
	"errors"
	"fmt"
)

func add(a, b int) int {
	return a + b
}

func processSomething(thing string) (string, error) {
	if thing == "Cool Thing" {
		return "processed successfully", nil
	}

	return "", errors.New("something bad happened")
}

func main() {
	greet := func(name string) {
		fmt.Println("Hello " + name)
	}

	greet("Cool Person")
	result := add(3, 4)
	fmt.Println(result)

	processingResult, err := processSomething("Not a Cool Thing")
	if err != nil {
		fmt.Println(err) //Go conditionals don't need to have parentheses
	} else {
		fmt.Println(processingResult)
	}
}
```

Functions can also be bound to Structs. This allows the function to have access to the function's private fields and act on its values.

```Go
package main

import (
	"fmt"
)

type Person struct {
	ID    int
	Name  string
	Phone string
}

func (person *Person) SayIntroduction() {
	fmt.Println("Hello! My name is " + person.Name)
}

func main() {
	person := Person{
		ID:    1,
		Name:  "Cool Person",
		Phone: "+1 111 1111-1111",
	}

	person.SayIntroduction()
}
```