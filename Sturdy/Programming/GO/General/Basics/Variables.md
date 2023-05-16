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
