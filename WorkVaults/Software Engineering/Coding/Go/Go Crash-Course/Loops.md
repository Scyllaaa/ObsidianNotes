Go only has one loop construct: `for`. The standard `for` loop consists of four components: the `init` statement, the condition expression, the statement that'll be executed after each iteration, and the loop body. Here's an example:

```Go
package main

import (
	"fmt"
)

func main() {
	for i := 0; i <= 10; i++ { //for i starting at zero, while i is less than or equal 10, increment i by one each iteraction
		fmt.Println(i)
	}
}
```

If you want a good old `while` loop, just drop the init statement and the post statement, like this:

```Go
package main

import (
	"fmt"
)

func main() {
	i := 0
	for i <= 10 { //for i starting at zero, while i is less than or equal 10, increment i by one each iteraction
		fmt.Println(i)
		i++
	}
}
```

Can you guess how to do an infinite loop?