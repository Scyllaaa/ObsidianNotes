package main
```Go
import (
	"fmt"
)

func main() {
	arr := [3]int{1, 2, 3}

	slice := arr[:]

	arr[1] = 42
	slice[2] = 27

	fmt.Println(arr, slice)
}
```

`[1 42 27] [1 42 27]`

```Go
package main

import (
	"fmt"
)

func main() {
	slice := []int{1, 2, 3}
	fmt.Println(slice)

	slice = append(slice, 4, 42, 27)
	fmt.Println(slice)
}
```

```Bash
[1 2 3] 
[1 2 3 4]
``` 


```Go
package main

import (
	"fmt"
)

func main() {
	slice := []int{1, 2, 3}
	fmt.Println(slice)

	slice = append(slice, 4, 42, 27)
	fmt.Println(slice)

	s2 := slice[1:]
	s3 := slice[:2]
	s4 := slice[1:2] // up to but not including index 2

	fmt.Println(s2, s3, s4)
}
```

```Bash
[1 2 3]
[1 2 3 4 42 27]
[2 3 4 42 27] [1 2] [2]
```