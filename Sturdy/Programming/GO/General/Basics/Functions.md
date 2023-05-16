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
