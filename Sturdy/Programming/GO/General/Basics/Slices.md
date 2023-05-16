## Slices
An array has a fixed size. A slice, on the other hand, is a dynamically-sized, flexible view into the elements of an array
The type `[]T` is a slice with elements of type `T`.
A slice is formed by specifying two indices, a low and high bound, separated by a colon:
```Go
a[low : high]
```
This selects a half-open range which includes the first element, but excludes the last one

- A slice does not store any data, it just describes a section of an underlying array
- Changing the elements of a slice modifies the corresponding elements of its underlying array
- Other slices that share the same underlying array will see those changes

<hr>

### Slice literals
A slice literal is like an array literal without the length.
This creates the array:
```Go
[3]bool{true, true, false}
```
Then builds a slice that references it:
```Go
[]bool{true, true, false}
```
<hr>

### Slice Defaults
- When slicing, you may omit the high or low bounds to use their defaults instead.
- The default is zero for the low bound and the length of the slice for the high bound.
For array
```Go
var a [10]int
```
these slice expressions are equivalent:
```Go
a[0:10]
a[:10]
a[0:]
a[:]
```

<hr>

### Length and Capacity
A slice has both a _length_ and a _capacity_.
==length== - the number of elements it contains
==capacity== - umber of elements in the underlying array, counting from the first element in the slice
The length and capacity of a slice `s` can be obtained using the expressions `len(s)` and `cap(s)`

```Go
func main() {
	s := []int{2, 3, 5, 7, 11, 13}
	printSlice(s)

	// Slice the slice to give it zero length.
	s = s[:0]
	printSlice(s)

	// Extend its length.
	s = s[:4]
	printSlice(s)

	// Drop its first two values.
	s = s[2:]
	printSlice(s)
}

func printSlice(s []int) {
	fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
}
```

### Nil slices
- The zero value of a slice is `nil`.
- A nil slice has a length and capacity of 0 and has no underlying array.
<hr>

### Make function
- Slices can be created with the built-in `make` function; this is how you create dynamically-sized arrays.
- The `make` function allocates a zeroed array and returns a slice that refers to that array:
``` Go
a := make([]int, 5)  // len(a)=5
```
To specify a capacity, pass a third argument to `make`:
```Go
b := make([]int, 0, 5) // len(b)=0, cap(b)=5

b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:]      // len(b)=4, cap(b)=4
```
<hr>

### Appending to Slice
```Go
func append(s []T, vs ...T) []T
```
- The first parameter `s` of `append` is a slice of type `T`, and the rest are `T` values to append to the slice
- The resulting value of `append` is a slice containing all the elements of the original slice plus the provided values
- append function returns a point to newly allocated array

### Range statement
- The `range` form of the `for` loop iterates over a slice or map.
- When ranging over a slice, two values are returned for each iteration. The first is the index, and the second is a copy of the element at that index.
```Go
var pow = []int{ 1, 2, 4, 8, 16, 32, 64, 128 }

func main() {
	for i, v := range pow {
		fmt.Printf("2**%d = %d\n", i, v)
	}
}
```
- You can skip the index or value by assigning to `_`
```Go
for i, _ := range pow
for _, value := range pow
```
- If you only want the index, you can omit the second variable.
```Go
for i := range pow
```
