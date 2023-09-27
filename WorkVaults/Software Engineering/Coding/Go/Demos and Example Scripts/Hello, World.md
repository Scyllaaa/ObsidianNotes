- create a folder
- initialize a module using the `go mod init demo`
- create a source file called `main.go`
- We need to have an entry point by creating a package called `main` and then creating the entypoint function called `main()`
main.go
```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, world!")
}
```
- Parameters live inside the match params
- Curly brackets marking the block that describes the main function
- run the program using `go run .` which compiles the program to a temporary directory and executes it from there 
-