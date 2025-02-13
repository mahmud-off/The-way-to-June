Tour of Go
- Каждая программа на `Go` состоит из пакетов, начиная свою с пакета `main` 
- Имя пакета совпадает с последним элементом пути импорта.
- Импорты могут быть как раздельно, так и в одной скобке, но хороший тон - в одной скобке
- В Go имя экспортируется, если оно начинается с заглавной буквы.

Функции
```
package main

import (
	"fmt"
)

func add(x int, y int) int{
	return x+y
}

func main(){
	fmt.Println(add(23,42))
}

```
Когда два или более последовательных именованных параметра функции имеют общий тип, вы можете исключить этот тип из всех, кроме последнего.
```
func add(x, y int) int {
	return x + y
}
```
Функция может возвращать любое количество результатов.
```
func swap(x, y string) (string, string) {
	return y, x
}
```
Возвращаемые значения Go могут иметь имена. Если это так, они обрабатываются как переменные, определенные в верхней части функции. Оператор return без аргументов возвращает именованные возвращаемые значения. Это называется "голым" возвратом.

Голые операторы return следует использовать только в коротких функциях, как в примере, показанном здесь. Они могут ухудшить читабельность при выполнении более длинных функций.
```
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```
Оператор var объявляет список переменных; как и в списках аргументов функций, тип является последним.

Оператор var может быть на уровне пакета или функции. В этом примере мы видим и то, и другое.
```
var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```
Объявление var может включать инициализаторы, по одному на переменную.

Если инициализатор присутствует, тип можно опустить; переменная примет тип инициализатора.
```
var i, j int = 1, 2

func main() {
	var c, python, java = true, false, "no!"
	fmt.Println(i, j, c, python, java)
}
```
Внутри функции оператор присваивания := short может использоваться вместо объявления var с неявным типом.

Вне функции каждый оператор начинается с ключевого слова (var, func и так далее), поэтому конструкция := недоступна.
```
func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"

	fmt.Println(i, j, k, c, python, java)
}
```
Go's basic types are

- bool
- string
- int  int8  int16  int32  int64
- uint uint8 uint16 uint32 uint64 uintptr
- byte // alias for uint8
- rune // alias for int32
     // represents a Unicode code point
- float32 float64
- complex64 complex128
Переменным, объявленным без явного начального значения, присваивается нулевое значение.
Нулевое значение равно:
- 0 для числовых типов, 
- false для логического типа и 
- "" (пустая строка) для строк.

Выражение T(v) преобразует значение v в тип T.
```
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)

ИЛИ

i := 42
f := float64(i)
u := uint(f)
```
В отличие от C, в Go назначение между элементами разного типа требует явного преобразования.

When the right hand side of the declaration is typed, the new variable is of that same type:
```
var i int
j := i // j is an int
```
But when the right hand side contains an untyped numeric constant, the new variable may be an `int`, `float64`, or `complex128` depending on the precision of the constant:
```
i := 42           // int
f := 3.142        // float64
g := 0.867 + 0.5i // complex128
```
Определение типа:
```
func main() {
	v := 18 // change me!
	fmt.Printf("v is of type %T\n", v)
}
```
## Constants
Constants are declared like variables, but with the `const` keyword.
Constants can be character, string, boolean, or numeric values.
Constants cannot be declared using the `:=` syntax.

Числовые константы - это значения высокой точности.
Нетипизированная константа принимает тип, необходимый для ее контекста.