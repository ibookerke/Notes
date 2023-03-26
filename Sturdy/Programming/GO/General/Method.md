# Methods
- We can define methods on types
- A method is a function with a special _receiver_ argument
- The receiver appears in its own argument list between the `func` keyword and the method name
- In this example, the `Abs` method has a receiver of type `Vertex` named `v`
```Go
type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	v := Vertex{3, 4}
	fmt.Println(v.Abs())
}
```
You can declare a method on non-struct types, too.
```Go
type MyFloat float64

func (f MyFloat) Abs() float64 {
	if f < 0 {
		return float64(-f)
	}
	return float64(f)
}
```
## Pointer Recievers
You can declare methods with pointer receivers.

This means the receiver type has the literal syntax `*T` for some type `T`. (Also, `T` cannot itself be a pointer such as `*int`.)

```Go
type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func (v *Vertex) Scale(f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}

func main() {
	v := Vertex{3, 4}
	v.Scale(10)
	fmt.Println(v.Abs())
}
```
Methods with pointer receivers can modify the value to which the receiver points (as `Scale` does here). Since methods often need to modify their receiver, pointer receivers are more common than value receivers.

### Methods and pointer indirections
Comparing using pointer recievers and function arguments you might notice that functions with a pointer argument must take a pointer:

```Go
var v Vertex
ScaleFunc(v, 5)  // Compile error!
ScaleFunc(&v, 5) // OK
```

while methods with pointer receivers take either a value or a pointer as the receiver when they are called:

```Go
var v Vertex
v.Scale(5)  // OK
p := &v
p.Scale(10) // OK
```

### Choosing a value of pointer receiver
There are two reasons to use a pointer receiver:
- The first is so that the method can modify the value that its receiver points to.
- The second is to avoid copying the value on each method call. This can be more efficient if the receiver is a large struct, for example.

In general, all methods on a given type should have either value or pointer receivers, but not a mixture of both.
