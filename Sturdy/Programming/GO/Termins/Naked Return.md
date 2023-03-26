

```Go
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```
A `return` statement without arguments returns the named return values.

Naked return statements should be used only in short functions, as with the example shown here. They can harm readability in longer functions.