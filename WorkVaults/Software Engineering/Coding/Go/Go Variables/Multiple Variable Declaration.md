In Go, it is possible to declare multiple variables in the same line using the `var ()`.

```Go
package main  
import ("fmt")  
  
func main() {  
  var a, b, c, d int = 1, 3, 5, 7  
  
  fmt.Println(a)  
  fmt.Println(b)  
  fmt.Println(c)  
  fmt.Println(d)  
}
```

**Note:** If you use the `type` keyword, it is only possible to declare **one type** of variable per line.
If the `type` keyword is not specified, you can declare different types of variables in the same line:
```Go
package main  
import ("fmt")  
  
func main() {  
  var a, b = 6, "Hello"  
  c, d := 7, "World!"  
  
  fmt.Println(a)  
  fmt.Println(b)  
  fmt.Println(c)  
  fmt.Println(d)  
}
```

## Go Variable Declaration in a Block

Multiple variable declarations can also be grouped together into a block for greater readability:
```Go
package main  
import ("fmt")  
  
func main() {  
   var (  
     a int  
     b int = 1  
     c string = "hello"  
   )  
  
  fmt.Println(a)  
  fmt.Println(b)  
  fmt.Println(c)  
}
```
