# Packages, Variables and function
Every Go program is made up of packages.
Program starts running in package `main`
## Import and Export
### Import statements:
```Go
- Good practice:
import (
	"fmt"
	"math"
)

- Which is equal to:

import "fmt"
import "math"

```
### Export
Exported names are always start with Captial letter 

<hr>

## Functions
### Casting types
- Type casting comes after the argument/function name
- You can also typecast multiple arguments
```Go
func add(x int, y int) int {
	return x + y
}
// Equivalent to:
func add(x, y int) int {
	return x + y
}
```

<hr>

### Return results
A function can return any number of results:
```Go
func swap(x, y string) (string, string) {
	return y, x
}


func main() {
	a, b := swap("hello", "world")
	fmt.Println(a, b)
}
```

<hr>

### Named return values
- Go's return values may be named. If so, they are treated as variables defined at the top of the function.
- These names should be used to document the meaning of the return values.
- Called [[Naked Return]].
```Go
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```

<hr>

## Variables
- The `var` statement declares a list of variables; as in function argument lists, the type is last.
- A `var` statement can be at package or function level. We see both in this example.
- if we don't assign values to variables they get the Zero Values
	- `0` for all integer types,
	- `0.0` for floating point numbers,
	- `false` for booleans,
	- `""` for strings,
	- `nil` for interfaces, slices, channels, maps, pointers and functions.
```Go
var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```

<hr>

### Vartiables with initializers
- If an initializer is present, the type can be omitted; the variable will take the type of the initializer.
```Go
var i, j int = 1, 2

func main() {
	var c, python, java = true, false, "no!"
	fmt.Println(i, j, c, python, java)
}
```

<hr>

### Short variable declaration
- Inside a function, the `:=` short assignment statement can be used in place of a `var` declaration with implicit type.
```Go
func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"
	fmt.Println(i, j, k, c, python, java)
}
```
- Outside a function, every statement begins with a keyword (`var`, `func`, and so on) and so the `:=` construct is not available.

<hr>

## Data Types
### Basic types
- bool
- string
- int  int8  int16  int32  int64
- uint uint8 uint16 uint32 uint64 uintptr // uintptr - pointer on data space
- byte // alias for uint8
- rune // alias for int32 | represents a Unicode code point
- float32 float64
- complex64 complex128

Variable declarations may be "factored" into blocks, as with import statements:
```Go
var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)
```

The `int`, `uint`, and `uintptr` types are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit systems. When you need an integer value you should use `int` unless you have a specific reason to use a sized or unsigned integer type.

<hr>

### Type Inference
When declaring a variable without specifying an explicit type (either by using the `:=` syntax or `var =` expression syntax), the variable's type is inferred from the value on the right hand side.

But when the right hand side contains an untyped numeric constant, the new variable may be an `int`, `float64`, or `complex128` depending on the precision of the constant:
```Go
i := 42           // int
f := 3.142        // float64
g := 0.867 + 0.5i // complex128
```

### Constants
- Constants are declared like variables, but with the `const` keyword.
- Constants cannot be declared using the `:=` syntax.

<hr>

# Flow Control statements
## For Loop
- Go has only one looping construct, the `for` loop.
``` Go
for i := 0; i < 10; i++ {
	sum += i
}
```
- The init and post statements are optional.
``` Go
for ; sum < 1000; {
	sum += sum
}
```
- At that point you can drop the semicolons: C's `while` is spelled `for` in Go.
``` Go
sum := 1
for sum < 1000 {
	sum += sum
}
```
- If you omit the loop condition it loops forever, so an infinite loop is compactly expressed.
```Go
for {
//do smth
}
```

<hr>

## if statement
- Like `for`, the `if` statement can start with a short statement to execute before the condition.
- Variables declared by the statement are only in scope until the end of the `if`.

- Like `for`, the `if` statement can start with a short statement to execute before the condition.
- Variables declared by the statement are only in scope until the end of the the conditional statement(`if, else if, else`).
```Go
func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	}
	return lim
}
```


<hr>

## switch statement
Go's switch is like the one in C, C++, Java, JavaScript, and PHP, except that Go only runs the selected case, not all the cases that follow. In effect, the `break` statement that is needed at the end of each case in those languages is provided automatically in Go. Another important difference is that Go's switch cases need not be constants, and the values involved need not be integers.

```Go
func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.GOOS; os {
	case "linux":
		fmt.Println("Linux.")
	case "darwin":
		fmt.Println("OS X.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}
```
- We can use `fallthrough` to turn off automatic `break` at the end of case statement 
- Switch cases evaluate cases from top to bottom, stopping when a case succeeds

Switch without a condition is the same as `switch true`.
```Go
func main() {
	t := time.Now()
	switch {
	case t.Hour() < 12:
		fmt.Println("Good morning!")
	case t.Hour() < 17:
		fmt.Println("Good afternoon.")
	default:
		fmt.Println("Good evening.")
	}
}
```
- This construct can be a clean way to write long if-then-else chains.

<hr>

## [[Defer Statement]]


<hr>

# Structs, Slices and Maps
## Pointers
Go has pointers. A pointer holds the memory address of a value.

The type `*T` is a pointer to a `T` value. Its zero value is `nil:
```Go
var p *int
```
The `&` operator generates a pointer to its operand:
```Go
i := 42
p = &i
```
The `*` operator denotes the pointer's underlying value.
```Go
fmt.Println(*p) // read i through the pointer p
*p = 21         // set i through the pointer p
```
This is known as "==dereferencing==" or "==indirecting=="

Unlike C, Go has no pointer arithmetic.

## Structs
A collection of fields
```Go
type Vertex struct {
	X int
	Y int
}
```
Fields are accessed using a dot
```Go
type Vertex struct {
	X int
	Y int
}
func main() {
	v := Vertex{1, 2}
	v.X = 4
	fmt.Println(v.X)
}
```

### Pointers to Structs
- Struct fields can be accessed through a struct pointer.
- To access the field `X` of a struct when we have the struct pointer `p` we could write `(*p).X`. However, that notation is cumbersome, so the language permits us instead to write just `p.X`, without the explicit dereference.

```Go
type Vertex struct {
	X int
	Y int
}

func main() {
	v := Vertex{1, 2}
	p := &v
	p.X = 1e9
	fmt.Println(v)
}
```

### Struct Literals
- A struct literal denotes a newly allocated struct value by listing the values of its fields
- You can list just a subset of fields by using the `Name:` syntax. (And the order of named fields is irrelevant.)
- The special prefix `&` returns a pointer to the struct value
```Go
type Vertex struct {
	X, Y int
}

var (
	v1 = Vertex{1, 2}  // has type Vertex
	v2 = Vertex{X: 1}  // Y:0 is implicit
	v3 = Vertex{}      // X:0 and Y:0
	p  = &Vertex{1, 2} // has type *Vertex
)

func main() {
	fmt.Println(v1, p, v2, v3)
}
```



<hr>

## Arrays
- The type `[n]T` is an array of `n` values of type `T`
```Go
var a [10]int
```
- An array's length is part of its type, so arrays cannot be resized

<hr>

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

<hr>

## Maps
- A map maps keys to values.
- The zero value of a map is `nil`. A `nil` map has no keys, nor can keys be added
- The `make` function returns a map of the given type, initialized and ready for use
```Go
type Vertex struct {
	Lat, Long float64
}

var m map[string]Vertex

func main() {
	m = make(map[string]Vertex)
	m["Bell Labs"] = Vertex{
		40.68433, -74.39967,
	}
	fmt.Println(m["Bell Labs"])
}
```

<hr>
### Map Literals
Like with structs but with keys
```Go
var m = map[string]Vertex{
	"Bell Labs": Vertex{
		40.68433, -74.39967,
	},
	"Google": Vertex{
		37.42202, -122.08408,
	},
}
```
<hr>
### Mutating Maps
```Go
m[key] = elem // Insert or update
elem = m[key] // retrieve
delete(m, key) // Delete an element
```
Test that a key is present with a two-value assignment:
```Go
elem, ok = m[key]
```
If `key` is in `m`, `ok` is `true`. If not, `ok` is `false`
If `key` is not in the map, then `elem` is the zero value for the map's element type

<hr>

### Function values
- Functions are values too. They can be passed around just like other values.
- Function values may be used as function arguments and return values.
```Go
func compute(fn func(float64, float64) float64) float64 {
	return fn(3, 4)
}

func main() {
	hypot := func(x, y float64) float64 {
		return math.Sqrt(x*x + y*y)
	}
	fmt.Println(hypot(5, 12))

	fmt.Println(compute(hypot))
	fmt.Println(compute(math.Pow))
}
```

### Function closures
- Go functions may be closures. A closure is a function value that references variables from outside its body. The function may access and assign to the referenced variables; in this sense the function is "bound" to the variables.
- For example, the `adder` function returns a closure. Each closure is bound to its own `sum` variable.
```Go
func adder() func(int) int {
	sum := 0
	return func(x int) int {
		sum += x
		return sum
	}
}

func main() {
	add:= adder()
	for i := 0; i < 10; i++ {
		fmt.Printf("%d => %d\n", i, add(i))
	}
}
```

