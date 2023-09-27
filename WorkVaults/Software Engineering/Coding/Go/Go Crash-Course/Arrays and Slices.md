An array is a data structure capable of storing ordered data that's accessible with indexes. In Go, arrays can be declared like so:

```js
fiveWords := [5]string{
	"zero",
	"one",
	"two",
	"three",
	"four",
}
fmt.Println(fiveWords)
```

This declares an array of five strings. An array can't be resized, but Go offers a few ways to work around that. To access the third value of the array, you could do the following:

```css
thirdWord := fiveWords[2]
fmt.Println(thirdWord)
```

This grabs the value at index 2 and assigns it to the variable thirdWord. Why index 2 if we wanted the third value? Because indexes start at zero 🙂

Slices, on the other hand, reference underlying arrays. This means that they can be resized - by pointing to a bigger array. If we wanted just the first two words of our fiveWords array, we could slice it like this:

```css
firstTwo := fiveWords[0:2]
fmt.Println(firstTwo)
```

This notation means "slice the array starting and including index 0 and finishing and excluding index 2." So we'll only get the values on indexes 0 and 1.

If we want to create a slice from scratch - instead of creating an array then slicing it - we could just omit the length:

```go
myOddsSlice := []int{1, 3, 5, 7, 9}
fmt.Println(myOddsSlice)
```

And if we want to add items to the slice, we can use the append function:

```go
myOddsSlice = append(myOddsSlice, 11, 13)
fmt.Println(myOddsSlice)
```

The append function takes a slice and any number of arguments to add to the slice. The arguments must be of the same type as the slice values.