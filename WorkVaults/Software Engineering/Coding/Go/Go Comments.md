
- A comment is a text that is ignored upon execution.
- Comments can be used to explain the code, and to make it more readable.
- Comments can also be used to prevent code execution when testing an alternative code.
- Go supports single-line or multi-line comments.
## Go Single-line Comments

Single-line comments start with two forward slashes (`//`).
Any text between `//` and the end of the line is ignored by the compiler (will not be executed).

```Go
package main  
import ("fmt")  
  
func main() {  
  fmt.Println("Hello World!") _// This is a comment_  
}
```
## Go Multi-line Comments

Multi-line comments start with `/*` and ends with `*/`.
Any text between `/*` and `*/` will be ignored by the compiler:

```Go
package main  
import ("fmt")  
  
func main() {  
  _/* The code below will print Hello World_  
  _to the screen, and it is amazing */_  
  fmt.Println("Hello World!")  
}
```