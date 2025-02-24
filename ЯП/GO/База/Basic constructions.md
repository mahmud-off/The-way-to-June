## For
В Go есть только одна циклическая конструкция, цикл for .
Базовый цикл for состоит из трех компонентов, разделенных точками с запятой:

- оператор init: выполняется перед первой итерацией 
- выражение условия: вычисляется перед каждой итерацией 
- оператор post: выполняется в конце каждой итерации

Оператор init часто представляет собой краткое объявление переменной, и объявленные в нем переменные видны только в области действия оператора for .

Цикл прекратит выполнение, как только логическое условие примет значение false .

Примечание: В отличие от других языков, таких как C, Java или JavaScript, здесь нет круглых скобок, окружающих три компонента оператора for, и всегда требуются фигурные скобки { }.
```
func main() {
	sum := 0
	for i := 0; i < 10; i++ {
		sum += i+10
	}
	fmt.Println(sum)
}
```
```
func main() {
	sum := 1
	for ; sum < 1000; {
		sum += sum
	}
	fmt.Println(sum)
}
```
## Go's "while"
```
func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}
```
## Бесконечный цикл
```
func main() {
	for {
	}
}
```
## IF
```
func sqrt(x float64) string {
	if x < 0 {
		return sqrt(-x) + "i"
	}
	return fmt.Sprint(math.Sqrt(x))
}

func main() {
	fmt.Println(sqrt(2), sqrt(-4))
}
```
Как и for , оператор if может начинаться с короткого оператора для выполнения перед условием.

Переменные, объявленные оператором, находятся в области видимости только до конца if .
```
func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	}
	return lim
}
```
## Switch
Switch Go's аналогичен переключателю в C, C ++, Java, JavaScript и PHP, за исключением того, что Go запускает только выбранный вариант, а не все последующие варианты. По сути, оператор break, который необходим в конце каждого обращения на этих языках, предоставляется автоматически в Go. Другое важное отличие заключается в том, что варианты переключения Go не обязательно должны быть константами, а используемые значения не обязательно должны быть целыми числами.
```
func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}
```
Switch without a condition is the same as `switch true`.
## Defer
Оператор defer откладывает выполнение функции до тех пор, пока не вернется окружающая функция.

Аргументы отложенного вызова вычисляются немедленно, но вызов функции не выполняется до тех пор, пока не вернется окружающая функция.
```
func main() {
	defer fmt.Println("world")

	fmt.Println("hello")
}

OUTPUT: 
hello
world
```
Отложенные вызовы функций помещаются в стек. Когда функция возвращается, ее отложенные вызовы выполняются в порядке поступления первыми.
```
func main() {
	fmt.Println("counting")

	for i := 0; i < 10; i++ {
		defer fmt.Println(i)
	}

	fmt.Println("done")
}
```
