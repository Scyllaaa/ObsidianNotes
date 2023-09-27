The range iterator can be used to traverse arrays, slices, and maps. When used on arrays and slices, it returns the index and the value of each iteration. When used on maps, it returns the key and the value of each iteration.

```Go
fiveWords := [5]string{
	"zero",
	"one",
	"two",
	"three",
	"four",
}

for index, value  := range fiveWords {
	message := fmt.Sprintf("index: %d - value: %s", index, value) //Sprintf takes a string template and values to interpolate
	fmt.Println(message)
}

numbers := map[string]int{}
numbers["one"] = 1
numbers["two"] = 2
numbers["three"] = 3

for key, value  := range numbers {
	message := fmt.Sprintf("key: %s - value: %d", key, value)
	fmt.Println(message)
}
```