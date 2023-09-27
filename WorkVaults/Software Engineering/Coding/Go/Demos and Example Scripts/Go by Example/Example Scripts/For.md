`for` is Go’s only looping construct. Here are some basic types of `for` loops.

```Go
package main

import "fmt"

func main() {

    i := 1
    for i <= 3 { // The most basic type, with a single condition.
        fmt.Println(i)
        i = i + 1
    }

    for j := 7; j <= 9; j++ { //A classic initial/condition/after `for` loop.
        fmt.Println(j)
    }

	for { /*`for` without a condition will loop repeatedly until you `break` out
		of the loop or `return` from the enclosing function. */
        fmt.Println("loop") 
        break
    }

    for n := 0; n <= 5; n++ { 
        if n%2 == 0 {
            continue // You can also `continue` to the next iteration of the loop.
        }
        fmt.Println(n)
    }
}
```

```Bash
$ go run for.go
1
2
3
7
8
9
loop
1
3
5
```
Next: [[If and Else|If/Else]] 