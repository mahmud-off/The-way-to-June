# GO's basic sintaxis 
```
// Основы языка GO

/*

  

**

Программа на языке Go хранится в одном или нескольких файлах.

Каждый файл с программным кодом должен принадлежать какому-нибудь пакету.

И вначале каждого файла должно идти объявление пакета, к которому этот файл принадлежит.

Пакет объявляется с помощью ключевого слова package.

  

*

В файле может использоваться функционал из других пакетов.

В этом случае используемые пакеты надо импортировать с помощью ключевого слова import.

Импортируемые пакеты должны идти после объявления пакета для текущего файла:

  

*/

package main // **

  

import (

    "fmt" // *

)

  

func main() { // Точка входа в программу (как в С++)

    //fmt.Println("Hello, this is GO")

    //fmt.Println("Hello, pupsik")

    //fmt.Println("Hello!")

  

    // ПЕРЕМЕННЫЕ

    // var имя_переменной тип_данных

  

    var hello string = "Hello, world"

    hello = "Hello, World!"

    fmt.Println(hello)

    var (

        name string = "Vadim"

        age  int    = 18

    )

  

    fmt.Println(name) //Vadim

    fmt.Println(age)  //18

  

    /*

        Краткое определение переменной

  

        имя_переменной := значение

  

        В этом случае тип данных явным образом не указывается, он выводится автоматически из присваиваемого значения.

        Ограничем такого способа является то, что его можно использовать только внутри функции.

  

    */

  

    name_2 := "Petr"

  

    fmt.Println(name_2)

  

    // КОНСТАНТЫ

  

    //Для определения констант применяется ключевое слово const вместо var

  

    const name_3 string = "Ivan"

    fmt.Println(name_3)

  

    const (

        age_4  int    = 12

        name_4 string = "Elena"

    )

  

    fmt.Println(age_4)

    fmt.Println(name_4)

  

    // АРИФМЕТИЧЕСКИЕ ОПЕРАЦИИ 1 В 1 КАК В с++ в плоть до инкрементов и декрементов

  

    // УСЛОВНЫЕ ВЫРАЖЕНИЯ 1 В 1 КАК В с++

  

    // ПОРЯЗРЯДНЫЕ ОПРЕЦАИИ 1 В 1 КАК В С++

  

    // МАССИВЫ

  

    var nums [5]int // инициализируется нулями

    fmt.Println(nums)

    var nums_2 [5]int = [5]int{1, 2, 3, 4, 5}

    fmt.Println(nums_2)

    // если кратко, то

    nums_3 := [5]int{6, 7, 8, 9, 10}

    fmt.Println(nums_3)

  

    //Если в квадратных скобках вместо длины указано троеточие, то длина массива определяется, исходя из количества переданных ему элементов:

  

    var numbers = [...]int{1, 2, 3, 4, 5} // длина массива 5

    numbers2 := [...]int{1, 2, 3}         // длина массива 3

    fmt.Println(numbers)                  // [1 2 3 4 5]

    fmt.Println(numbers2)                 // [1 2 3]

  

    /*

        При этом длина массива является частью его типа. И, к примеру, следующие два массива представляют разные типы данных, хотя они и хранят данные одного типа:

  

        1

        2

        3

        var numbers [3]int = [3]int{1, 2, 3}

        var numbers2 [4]int = [4]int{1, 2, 3, 4}

        numbers = numbers2  // ! Ошибка

        И в данном случае при присвоении мы получим ошибку, так как данные одного типа пытаемся передать переменной другого типа.

    */

  

    //индексы как и везде

    fmt.Println(numbers[2])

    numbers[2] = 87

    fmt.Println(numbers[2])

  

    //Индексы массива как ключи

    colors := [3]string{2: "blue", 0: "red", 1: "green"}

    fmt.Println(colors[2]) // blue

  

    //УСЛОВНЫЕ КОНСТРУКЦИИ 1 В 1 КАК В С++ разве что условние не ставится в скобочки. Аналогично с конструкцией Switch...case

  

    // ЦИКЛЫ

  

    /*

        Циклы позволяют в зависимости от определенного условия выполнять некоторые действия множество раз.

        Фактически в Go есть только один цикл - цикл for, который может принимать разные формы.

        Этот цикл имеет следующее формальное определение:

        for [инициализация счетчика]; [условие]; [изменение счетчика]{

        // действия

        }

    */

  

    for i := 0; i < 10; i++ {

        fmt.Print(i)

        fmt.Print(" ")

    }

  

    /*

                var i = 1

                for ; i < 10; i++{

                    fmt.Println(i * i)

                }

  

                или

  

                var i = 1

                for ; i < 10;{

                fmt.Println(i * i)

                i++

                }

  

                или

  

                var i = 1

                for i < 10{

                fmt.Println(i * i)

                i++

                }

    */

  

    fmt.Println()

  

    for i := 1; i < 10; i++ {

        for j := 1; j < 10; j++ {

            fmt.Print(j*i, " ")

        }

        fmt.Println()

    }

  

    // ПЕРЕБОР МАССИВОВ

  

    var users = [3]string{"Tom", "Alice", "Kate"}

    for index, value := range users {

        fmt.Println(index, value)

    }

    // или же

    /*

        Если мы не планируем использовать значения или индексы элементов, то мы можем вместо них указать прочерк. Например, нам не нужны индексы:

  

        for _, value := range users{

            fmt.Println(value)

        }

  

        Но также для перебора массива можно использовать и стандартную версию цикла for:

  

        var users = [3]string{"Tom", "Alice", "Kate"}

        for i:= 0; i < len(users); i++{

            fmt.Println(users[i])

        }

    */

  

    // Break и continue 1 в 1 как в с++

  

    // ФУНКЦИЯ

  

    /*

        func имя_функции (список_параметров) (типы_возвращаемых_значений){

        выполняемые_операторы

        }

    */

  

    hallo()

    hallo()

    hallo()

  

    //параметры

  

    parametr(1)

    parametrs(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11)

  

    //возврат результата фанкции

  

    /*

        func имя_функции (список_параметров) тип_возвращаемого_значения {

        выполняемые_операторы

        return возвращаемое_значение

        }

    */

  

    var c int = summ(15, 15)

    fmt.Println(c)

  

    // В GO ФУНКЦИЯ МОЖЕТ ВОЗВРАЩАТЬ НЕСКОЛЬКО ЗНАЧЕНИЙ

  

    /*

  

        func add(x, y int, firstName, lastName string) (int , string) {

        var z int = x + y

        var fullName = firstName + " " + lastName

        return z, fullName

        }

  

    */

  

    // ТАКЖЕ ФУНКЦИЯ МОЖЕТ БЫТЬ ПАРАМЕТРОМ/ВОЗВРАЩАЕМЫМ ЗНАЧЕНИЕМ ДЛЯ ДРУГОЙ ФУНКЦИИ

  

    /*

  

        func add(x int, y int) int{ return x + y}

        func subtract(x int, y int) int{ return x - y}

        func multiply(x int, y int) int{ return x * y}

  

        func selectFn(n int) (func(int, int) int){

            if n==1 {

                return add

            }else if n==2{

                return subtract

            }else{

                return multiply

            }

        }

  

        func main() {

  

            f := selectFn(1)

            fmt.Println(f(3, 4))        // 7

  

            f = selectFn(3)

            fmt.Println(f(3, 4))        // 12

        }

  

    */

  

    // АНОНИМНАЯ ФУНКЦИЯ (аналог lambda функции)

  

    //Анонимные функции - это функции, которым не назначено имя.

    // Они отличаются от обычных функций также тем, что они могут определяться внутри других функций и также могут иметь доступ к контексту выполнения.

  

    f := func(x, y int) int { return x + y }

    fmt.Println(f(3, 4)) // 7

    fmt.Println(f(6, 7)) // 13

  

    // АНОНИМНАЯ ФУНКЦИЯ МОЖЕТ БЫТЬ АРГУМЕНТОМ/ЗНАЧЕНИЕМ обычной функции

  

    // Рекурсия как и везде

  

    //defer

    /*

  

        Оператор defer позволяет выполнить определенную функцию в конце программы, при этом не важно, где в реальности вызывается эта функция.

  

        func main() {

            defer finish()

            fmt.Println("Program has been started")

            fmt.Println("Program is working")

        }

  

        func finish(){

            fmt.Println("Program has been finished")

        }

  

    */

  

    //panic

    // Обработчик ошибок

    /*

        func main() {

            fmt.Println(divide(15, 5))

            fmt.Println(divide(4, 0))

            fmt.Println("Program has been finished")

        }

        func divide(x, y float64) float64{

            if y == 0{

                panic("Division by zero!")

            }

            return x / y

        }

    */

  

}

  

func parametr(x int) {

    fmt.Println(x)

}

  

func parametrs(nums ...int) {

    var sum int = 0

    for _, number := range nums {

        sum += number

    }

    fmt.Println(sum)

  

}

  

func hallo() {

    fmt.Println("Hello, World!!!")

}

  

func summ(a int, b int) int {

    return a + b

}
```