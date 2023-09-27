Maps can be used whenever you want to pair a specific key with a value. Map declarations have their key and value types specified:

```Go
numbers := map[string]int{}
numbers["one"] = 1
numbers["two"] = 2
numbers["three"] = 3
fmt.Println(numbers)
```

If you check the printed result, you might notice that the map is not ordered like the array. Never take a map's standard ordering as a given. Instead, always pick the values by the keys.