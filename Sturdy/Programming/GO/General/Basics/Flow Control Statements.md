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
