A defer statement defers the execution of a function until the surrounding function returns.

The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.

```Go
func main() {
	defer fmt.Println("world")
	defer fmt.Println("lala")

	fmt.Println("hello")
}
```

The defer statement uses stack for storing the execution sequence

[More about defers](https://go.dev/blog/defer-panic-and-recover)

