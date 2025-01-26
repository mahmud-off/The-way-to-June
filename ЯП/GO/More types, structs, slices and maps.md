## Pointers
GO имеет указатели. Указатель содержит адрес значения в памяти.

- Тип * T является указателем на значение T. Его нулевое значение равно nil .
	`var p * int`
- Оператор & генерирует указатель на свой операнд.
```
i := 42
p = &i
```
- Оператор * обозначает базовое значение указателя.
- `fmt.Println(*p)` // считываем i с помощью указателя p
- `*p = 21`// устанавливаем i с помощью указателя p. Это известно как "разыменование" или "косвенное обращение".
- ***В отличие от C, в Go нет арифметики указателей.***
## Structs
- Структура - это набор полей.
```
type Vertex struct {
	X int
	Y int
}

func main() {
	fmt.Println(Vertex{1, 2})
}
```
- Struct fields are accessed using a dot.
```
  func main() {
	v := Vertex{1, 2}
	v.X = 4
	fmt.Println(v.X)
}
```
- Struct fields can be accessed through a struct pointer.
Чтобы получить доступ к полю X структуры, когда у нас есть указатель структуры p, мы могли бы написать (*p).X . Однако эта запись громоздка, поэтому язык позволяет нам вместо этого писать просто p.X без явного разыменования.
```
func main() {
	v := Vertex{1, 2}
	p := &v
	p.X = 1e9
	fmt.Println(v)
}
```
Структурный литерал обозначает вновь выделенное значение struct, перечисляя значения его полей.

Вы можете перечислить только подмножество полей, используя синтаксис Name: . (Порядок именованных полей не имеет значения.)

Специальный префикс & возвращает указатель на значение структуры.
```
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
## Arrays
Тип `[n]T` представляет собой массив из n значений типа T.

Выражение `var a [10]int` объявляет переменную a как массив из десяти целых чисел.

Длина массива является частью его типа, поэтому размер массивов изменять нельзя. Это кажется ограничивающим, но не волнуйтесь; Go предоставляет удобный способ работы с массивами.
```
func main() {
	var a [2]string
	a[0] = "Hello"
	a[1] = "World"
	fmt.Println(a[0], a[1])
	fmt.Println(a)

	primes := [6]int{2, 3, 5, 7, 11, 13}
	fmt.Println(primes)
}
```
## Slices
- Массив имеет фиксированный размер. Срез, с другой стороны, представляет собой динамически изменяемый вид элементов массива. На практике срезы встречаются гораздо чаще, чем массивы.
- Тип `[]T` представляет собой срез с элементами типа `T`.
- Срез формируется путем указания двух индексов, нижней и верхней границы, разделенных двоеточием: `a[low : hight]`
- При этом выбирается полуоткрытый диапазон, который включает первый элемент, но исключает последний.
- Следующее выражение создает срез, который включает элементы с 1 по 3 из a: `a[1:4]`
```
func main() {
	primes := [6]int{2, 3, 5, 7, 11, 13}

	var s []int = primes[1:4]
	fmt.Println(s)
}
```
## Slices are like references to arrays (срез - ссылка на элементы массива)
- Фрагмент не хранит никаких данных, он просто описывает часть базового массива.
- Изменение элементов фрагмента изменяет соответствующие элементы его базового массива.
- Другие фрагменты, которые совместно используют тот же базовый массив, увидят эти изменения.
```
func main() {
	names := [4]string{
		"John",
		"Paul",
		"George",
		"Ringo",
	}
	fmt.Println(names)

	a := names[0:2]
	b := names[1:3]
	fmt.Println(a, b)

	b[0] = "XXX"
	fmt.Println(a, b)
	fmt.Println(names)
}
```
## Slice literals
- Литерал среза подобен литералу массива без указания длины.
- Это литерал массива:
	[3]bool{true, true, false}
- И это создает тот же массив, что и выше, затем создает срез, который ссылается на него.:
	[]bool{истина, true, false}
```
func main() {
	s := []int{2, 3, 5, 7, 11, 13}

	s = s[1:4]
	fmt.Println(s)

	s = s[:2]
	fmt.Println(s)

	s = s[1:]
	fmt.Println(s)
}
```
## Slice defaults
- При нарезке вы можете опустить верхние или нижние границы, чтобы вместо них использовать значения по умолчанию.
- По умолчанию для нижней границы равно нулю, а для верхней границы - длине среза.
- Для массива `var a [10]int` 
эти выражения среза эквивалентны:
```
a[0:10]
a[:10]
a[0:]
a[:]
```
## Slice length and capacity
- Срез имеет как длину (length), так и вместимость(capacity).
- Длина фрагмента - это количество элементов, которые он содержит.
- Емкость фрагмента - это количество элементов в базовом массиве, считая от первого элемента в фрагменте.
- Длину и вместимость ломтика (ов) можно получить, используя выражения `len` (ов) и `cap` (ов).
- Вы можете увеличить длину ломтика, нарезав его повторно, при условии, что он имеет достаточную вместимость. Попробуйте изменить одну из операций срезания в примере программы, чтобы расширить ее возможности, и посмотрите, что произойдет.
```
func PrintSlice(s []int) {
    fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
}

func main() {
    a := [5]int{0, 1, 2, 3, 4}
    s := a[2:]
    PrintSlice(s)
}
```
## Nil slices
- Нулевое значение фрагмента равно нулю.
- Фрагмент с нулевым значением имеет длину и емкость 0 и не имеет базового массива.
```
func main() {
	var s []int
	fmt.Println(s, len(s), cap(s))
	if s == nil {
		fmt.Println("nil!")
	}
}
```
## Creating a slice with make
- Фрагменты могут быть созданы с помощью встроенной функции `make`; именно так создаются массивы динамического размера.
- Функция `make` выделяет обнуленный массив и возвращает фрагмент, который ссылается на этот массив.:
`a := make([]int, 5) // len(a)=5`
Чтобы указать емкость, передайте третий аргумент make:
```
b := make([]int, 0, 5) // len(b)=0, cap(b)=5
b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:] // len(b)=4, cap(b)=4
```
## Slices of slices
- Срезы могут содержать любой тип, включая другие срезы.
```
func main() {
	// Create a tic-tac-toe board.
	board := [][]string{
		[]string{"_", "_", "_"},
		[]string{"_", "_", "_"},
		[]string{"_", "_", "_"},
	}

	// The players take turns.
	board[0][0] = "X"
	board[2][2] = "O"
	board[1][2] = "X"
	board[1][0] = "O"
	board[0][2] = "X"

	for i := 0; i < len(board); i++ {
		fmt.Printf("%s\n", strings.Join(board[i], " "))
	}
}
```
## Appending to a slice
- Добавление новых элементов к фрагменту является обычным делом, и поэтому Go предоставляет встроенную функцию добавления. Документация встроенного пакета описывает append . `func append(s []T, vs ...T) []T`
- Первый параметр `s` функции append представляет собой фрагмент типа `T`, а остальные - это значения `T`, которые нужно добавить к фрагменту.
- Результирующее значение append представляет собой фрагмент, содержащий все элементы исходного фрагмента плюс предоставленные значения.
- Если вспомогательный массив `s` слишком мал, чтобы вместить все заданные значения, будет выделен массив большего размера. Возвращенный фрагмент будет указывать на только что выделенный массив.
```
func main() {
	var s []int
	printSlice(s)

	// append works on nil slices.
	s = append(s, 0)
	printSlice(s)

	// The slice grows as needed.
	s = append(s, 1)
	printSlice(s)

	// We can add more than one element at a time.
	s = append(s, 2, 3, 4)
	printSlice(s)
}

func printSlice(s []int) {
	fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
}
```
## Range
- Форма диапазона цикла for выполняет итерацию по срезу или карте.
- При ранжировании по срезу для каждой итерации возвращаются два значения. Первый - это индекс, а второй - копия элемента с этим индексом.
```
var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}

func main() {
	for i, v := range pow {
		fmt.Printf("2**%d = %d\n", i, v)
	}
}
```
- Вы можете пропустить индекс или значение, присвоив ему значение `_`.
```
for i, _ := range pow
for _, value := range pow
```
- Если вам нужен только индекс, вы можете опустить вторую переменную.
```
for i := range pow
```
## Maps
- A map maps keys to values.
- The zero value of a map is `nil`. A `nil` map has no keys, nor can keys be added.
- The `make` function returns a map of the given type, initialized and ready for use.
```
type Vertex struct {
	Lat, Long float64
	name string
}

var m map[string]Vertex

func main() {
	m = make(map[string]Vertex)
	m["Bell Labs"] = Vertex{
		40.68433, -74.39967, "Вадим",
	}
	fmt.Println(m["Bell Labs"])
}

```
- Map literals are like struct literals, but the keys are required.
```
type Vertex struct {
	Lat, Long float64
}

var m = map[string]Vertex{
	"Bell Labs": Vertex{
		40.68433, -74.39967,
	},
	"Google": Vertex{
		37.42202, -122.08408,
	},
}
```
- Если тип верхнего уровня - это просто имя типа, вы можете опустить его из элементов литерала.
```
var m = map[string]Vertex{
	"Bell Labs": {40.68433, -74.39967},
	"Google":    {37.42202, -122.08408},
}
```
## Mutating Maps
- Insert or update an element in map `m`: `m[key] = elem`
- Retrieve an element: `elem = m[key]`
- Delete an element: `delete(m, key)`
- Test that a key is present with a two-value assignment: `elem, ok = m[key]`
- If `key` is in `m`, `ok` is `true`. If not, `ok` is `false`.
- If `key` is not in the map, then `elem` is the zero value for the map's element type.
- **Note:** If `elem` or `ok` have not yet been declared you could use a short declaration form: `elem, ok := m[key]`
## Function values
- Functions are values too. They can be passed around just like other values.
- Function values may be used as function arguments and return values.
```import (
	"fmt"
	"math"
)

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
## Function closures (рекурсия)
- Функции Go могут быть **closures**. **Closures** - это значение функции, которое ссылается на переменные извне своего тела. Функция может обращаться к переменным, на которые даны ссылки, и присваивать их; в этом смысле функция "привязана" к переменным.
```
func adder() func(int) int {
	sum := 0
	return func(x int) int {
		sum += x
		return sum
	}
}

// fibonacci is a function that returns
// a function that returns an int.
func fibonacci() func() int {
    first, second := 0, 1
    return func() int {
        ret := first
        first, second = second, first+second
        return ret
    }
}
```
