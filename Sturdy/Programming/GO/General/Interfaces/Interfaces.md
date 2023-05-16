# Interfaces
- An _interface type_ is defined as a set of [[Method]] signatures.
- A value of interface type can hold any value that implements those [[Method]]s
```Go
type MyFloat float64
type Vertex struct {
	X, Y float64
}

type Abser interface {
	Abs() float64
}

func (f MyFloat) Abs() float64 {
	if f < 0 {
		return float64(-f)
	}
	return float64(f)
}

func (v *Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	var a, b Abser
	f := MyFloat(-math.Sqrt2)
	v := Vertex{3, 4}

	a = f  // a MyFloat implements Abser
	b = &v // a *Vertex implements Abser

	fmt.Println(a.Abs())
	fmt.Println(b.Abs())
}
```

## Interfaces are implemented implicitly 
- A type implements an interface by implementing its [[Method]]s. There is no explicit declaration of intent, no "implements" keyword.

- Implicit interfaces decouple the definition of an interface from its implementation, which could then appear in any package without prearrangement.

```Go
type I interface {
	M()
}

type T struct {
	S string
}

// This method means type T implements the interface I,
// but we don't need to explicitly declare that it does so.
func (t T) M() {
	fmt.Println(t.S)
}

func main() {
	var i I = T{"hello"}
	i.M()
}
```


## Interface Values
Under the hood, interface values can be thought of as a tuple of a value and a concrete type:
```Go
(value, type)
```
An interface value holds a value of a specific underlying concrete type.

Calling a [[Method]] on an interface value executes the [[Method]] of the same name on its underlying type.
```Go
type I interface {
	M()
}

type T struct {
	S string
}

func (t *T) M() {
	fmt.Println(t.S)
}

type F float64

func (f F) M() {
	fmt.Println(f)
}
```

## Interface values with nil underlying values
If the concrete value inside the interface itself is nil, the [[Method]] will be called with a nil receiver.

In some languages this would trigger a null pointer exception, but in Go it is common to write [[Method]]s that gracefully handle being called with a nil receiver (as with the method `M` in this example.)
```Go
func main() {
	var i I

	var t *T
	describe(i) // runtime error since there is not type
	i = t
	describe(i) // print (<nil>, *main.T)
	i.M()

	i = &T{"hello"}
	describe(i) // print (&{hello}, *main.T)
	i.M()
}
```

## Empty Interface
The interface type that specifies zero methods is known as the _empty interface_:
```Go
interface{}
```
An empty interface may hold values of any type. (Every type implements at least zero methods.)

Empty interfaces are used by code that handles values of unknown type. For example, `fmt.Print` takes any number of arguments of type `interface{}`.

A _type assertion_ provides access to an interface value's underlying concrete value.

## Type Assertions
- A _type assertion_ provides access to an interface value's underlying concrete value.
```Go
t := i.(T)
```
This statement asserts that the interface value `i` holds the concrete type `T` and assigns the underlying `T` value to the variable `t`.
If `i` does not hold a `T`, the statement will trigger a panic.
To _test_ whether an interface value holds a specific type, a type assertion can return two values: the underlying value and a boolean value that reports whether the assertion succeeded.
```Go
t, ok := i.(T)
```
Example:
```Go
func main() {
	var i interface{} = "hello"

	s := i.(string)
	fmt.Println(s) //pritng hello

	s, ok := i.(string)
	fmt.Println(s, ok) //print hello true

	f, ok := i.(float64)
	fmt.Println(f, ok) //print 0 false

	f = i.(float64) // panic
	fmt.Println(f)
}

```

## [[Type switches]]
Example:
```Go
func do(i interface{}) {
	switch v := i.(type) {
	case int:
		fmt.Printf("Twice %v is %v\n", v, v*2)
	case string:
		fmt.Printf("%q is %v bytes long\n", v, len(v))
	default:
		fmt.Printf("I don't know about type %T!\n", v)
	}
}

func main() {
	do(21)
	do("hello")
	do(true)
}
```

## Stringers
One of the most ubiquitous interfaces is [`Stringer`](https://go.dev/pkg/fmt/#Stringer) defined by the [`fmt`](https://go.dev/pkg/fmt/) package.

```Go
type Stringer interface {
    String() string
}
```

A `Stringer` is a type that can describe itself as a string. The `fmt` package (and many others) look for this interface to print values

Example:
```Go
type Person struct {
	Name string
	Age  int
}

func (p Person) String() string {
	return fmt.Sprintf("%v (%v years)", p.Name, p.Age)
}

func main() {
	a := Person{"Arthur Dent", 42}
	z := Person{"Zaphod Beeblebrox", 9001}
	fmt.Println(a, z)
}
```
