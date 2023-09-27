_Maps_ are Go’s built-in [associative data type](https://en.wikipedia.org/wiki/Associative_array) (sometimes called _hashes_ or _dicts_ in other languages).
```Go 
package main

import (
    "fmt"
    "maps"
)

func main() {

/* To create an empty map, use the builtin `make`: `make(map[key-type]val-type)`.*/ 
    m := make(map[string]int)

// Set key/value pairs using typical `name[key] = val` syntax.
    m["k1"] = 7
    m["k2"] = 13


    fmt.Println("map:", m) // Printing a map with e.g. `fmt.Println` will show all of its key/value pairs.

    v1 := m["k1"] // Get a value for a key with `name[key]`.
    fmt.Println("v1:", v1) 

    v3 := m["k3"] // // If the key doesn’t exist, the [zero value](https://go.dev/ref/spec#The_zero_value) of the value type is returned.
    fmt.Println("v3:", v3) 

    fmt.Println("len:", len(m))// The builtin `len` returns the number of key/value pairs when called on a map.

    delete(m, "k2") // The builtin `delete` removes key/value pairs from a map.
    fmt.Println("map:", m)

    clear(m) // To remove _all_ key/value pairs from a map, use the `clear` builtin.
    fmt.Println("map:", m)

/* The optional second return value when getting a value from a map indicates if the key was present in the map. This can be used to disambiguate between missing keys and keys with zero values like `0` or `""`. Here we didn’t need the value itself, so we ignored it with the _blank identifier_ `_`*/
    _, prs := m["k2"]
    fmt.Println("prs:", prs)

    n := map[string]int{"foo": 1, "bar": 2} // You can also declare and initialize a new map in the same line with this syntax.
    fmt.Println("map:", n)

    n2 := map[string]int{"foo": 1, "bar": 2} // The `maps` package contains a number of useful utility functions for maps.
    if maps.Equal(n, n2) {
        fmt.Println("n == n2")
    }
}
```

Note that maps appear in the form `map[k:v k:v]` when printed with `fmt.Println`.
```Shell
$ go run maps.go 
map: map[k1:7 k2:13]
v1: 7
v3: 0
len: 2
map: map[k1:7]
map: map[]
prs: false
map: map[bar:2 foo:1]
n == n2
```

Next: [[Range]]