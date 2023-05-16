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
