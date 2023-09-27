Problem
```Go
i := 1
println(i++) // ???
println(++i) // ???
```

Solution: Increment and decrements are statements in Go.
```Go
i := 1
i++
println(i) // 2
i++
println(i) // 3
```


```Go
for i := 0; i <5; i++  # Loop with incrementor
for i < ... 3 loop till condition
for # infinite loop
for user := range users # loop over collection
```
- All loops in Go are for-loops!
