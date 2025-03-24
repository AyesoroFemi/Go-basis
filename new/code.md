
# Go Programming Basics

## 📌 Variables and Pointers in Go

### 🔸 Variable Declarations

Go supports two main ways of declaring variables:

```go
// Explicit declaration with type
var myLocation string = "Nigeria, Lagos"

// Short variable declaration (type inferred)
p := "Johnny"
```

### 🔸 Global vs Local Variables

- **Global variables** are declared outside of any function and accessible throughout the package.
- **Local variables** are declared inside a function and only accessible within that function's scope.

### 🔸 Example Code:
```go
package main

import "fmt"

func main() {
    var myLocation string = "Nigeria, Lagos"
    p := "Johnny"

    fmt.Println(&p) // Prints the memory address of 'p'
    fmt.Printf("Dereferencing the variable value %v\n", p)
    fmt.Println(myLocation)
}
```

---

## 🧠 Pointers in Go

### What is a Pointer?
A pointer holds the **memory address of another variable**. Go uses pointers for reference-based programming and memory optimization.

### Why Use Pointers?
- Avoid copying large structs.
- Modify values inside functions.
- Efficient memory usage.

### Example Code:
```go
package main

import "fmt"

func main() {
    var x int = 10
    var p *int = &x // 'p' is a pointer to 'x'

    fmt.Println("Value of x:", x)
    fmt.Println("Memory address of x:", p)
    fmt.Println("Dereferenced value:", *p)

    var isLoggedIn bool = true
    if isLoggedIn {
        fmt.Println("Welcome back!")
    }
}
```



## 🧠 Functions in Go

Functions are the building blocks of any Go program. Here's a comprehensive guide to how functions work in Go.

---

### ✅ Basic Function

```go
package main

import "fmt"

func greet() {
    fmt.Println("Hello from a function!")
}

func main() {
    greet()
}
```

---

### ✅ Functions as Values (Function as Data)

```go
package main

import "fmt"

func add(a, b int) int {
    return a + b
}

func main() {
    var myFunc func(int, int) int = add
    result := myFunc(5, 3)
    fmt.Println("Result:", result)
}
```

---

### ✅ Order of Functions Does Not Matter

```go
package main

import "fmt"

func main() {
    sayHi()
    sayBye()
}

func sayBye() {
    fmt.Println("Goodbye!")
}

func sayHi() {
    fmt.Println("Hi there!")
}
```

---

### ✅ Breaking Problems into Smaller Tasks

```go
package main

import "fmt"

func calculateArea(length, width float64) float64 {
    return length * width
}

func main() {
    l := 10.0
    w := 5.0
    area := calculateArea(l, w)
    fmt.Println("Area:", area)
}
```

---

### ✅ Code Reuse (DRY Principle)

```go
package main

import "fmt"

func printMessage(name string) {
    fmt.Println("Hello,", name)
}

func main() {
    printMessage("Alice")
    printMessage("Bob")
    printMessage("Charlie")
}
```

---

## 🛠 Types of Functions in Go

### 1️⃣ Normal Functions with Identifier

```go
package main

import "fmt"

func multiply(a int, b int) int {
    return a * b
}

func main() {
    result := multiply(4, 5)
    fmt.Println("Multiplication:", result)
}
```

---

### 2️⃣ Anonymous or Lambda Functions

```go
package main

import "fmt"

func main() {
    sum := func(a int, b int) int {
        return a + b
    }
    fmt.Println("Sum:", sum(2, 3))
}
```

---

### 3️⃣ Methods (Functions Associated with Structs)

```go
package main

import "fmt"

type Rectangle struct {
    length, width float64
}

func (r Rectangle) area() float64 {
    return r.length * r.width
}

func main() {
    rect := Rectangle{10, 5}
    fmt.Println("Area:", rect.area())
}
```

---

### ✍️ Function Signature

```go
// This is a function signature:
func divide(a float64, b float64) float64 {
    return a / b
}
```

---

### 🔁 Returning Values from a Function

```go
package main

import "fmt"

func greet(name string) string {
    return "Hello, " + name
}

func main() {
    message := greet("Jane")
    fmt.Println(message)
}
```

---

### 🔁 Returning Multiple Values

```go
package main

import "fmt"

func divideAndRemainder(a, b int) (int, int) {
    return a / b, a % b
}

func main() {
    q, r := divideAndRemainder(10, 3)
    fmt.Println("Quotient:", q, "Remainder:", r)
}
```

---

### 📦 Pass by Value

```go
package main

import "fmt"

func changeValue(x int) {
    x = 100
}

func main() {
    a := 10
    changeValue(a)
    fmt.Println("a is still:", a) // Value not changed
}
```

---

### 🔗 Pass by Reference (Using Pointers)

```go
package main

import "fmt"

func changeValue(x *int) {
    *x = 100
}

func main() {
    a := 10
    changeValue(&a)
    fmt.Println("a is now:", a) // Value changed
}
```




# Arrays, Slices, Maps, Structs, Pointers & Interfaces in Go

## Arrays

> “An array in Go is a value type”, meaning arrays are copied entirely when assigned to another variable or passed to a function.  
> This is different from reference types like slices, maps, or pointers.

- A value type in Go means assignments or function calls create a copy of the data.
- Changes made to the copy do **not** affect the original.

```go
var numbers [3]int = [3]int{1, 2, 3}
var numbers [3]int
fmt.Printf("What are the nos in this collection %d\n", numbers)
```

### Arrays Passed to Functions

```go
func changeArray(arr [3]int) {
    arr[0] = 99
    fmt.Println("Inside function:", arr)
}

func main() {
    original := [3]int{1, 2, 3}
    changeArray(original)
    fmt.Println("Outside function:", original)
}
```

### Contrast with Slices

```go
func changeSlice(s []int) {
    s[0] = 99
    fmt.Println("Inside function:", s)
}

func main() {
    original := []int{1, 2, 3}
    changeSlice(original)
    fmt.Println("Outside function:", original)
}
```

---

## Slices

- A slice is a flexible, dynamic-sized view into an array.
- A slice has:
  - Pointer to the underlying array
  - Length
  - Capacity

```go
fruits := []string{"apple", "banana", "cherry"}

users := []string{"Alice", "Bob", "Charlie"}
users = append(users, "Diana")
fmt.Println("User list:", users)
```

### Modifying the Original Data

```go
numbers := []int{1, 2, 3, 4}
sub := numbers[1:3] // [2, 3]
sub[0] = 99         // affects original slice
fmt.Println(numbers) // [1, 99, 3, 4]
```

### Loop in Slice — `for range`

```go
seasons := []string{"Spring", "Summer", "Autumn", "Winter"}
for ix, season := range seasons {
    fmt.Printf("Season %d is: %s\n", ix, season)
}

var season string
for _, season = range seasons {
    fmt.Printf("%s\n", season)
}
```

---

## Maps

```go
person := map[string]string{"name": "Alice", "city": "Lagos"}

var getUserProfile map[int]string
fmt.Println(getUserProfile)

userProfile := map[string]string{
    "name": "John",
    "email": "john@example.com",
}
fmt.Println("Name:", userProfile)
```

---

## Structs

```go
type Task struct {
    Title string
    Done  bool
}

func AddTask(tasks []Task, title string) []Task {
    t := Task{Title: title}
    return append(tasks, t)
}

newTask := []Task{
    {Title: "Go programming", Done: false},
    {Title: "Java", Done: true},
}

fmt.Println(newTask)

// var todos []Task
// todos = AddTask(todos, "Learn Pointers")
// todos = AddTask(todos, "Master Interfaces")
// fmt.Println(todos)
```

### Pointers with Structs (Modifying Data Directly)

```go
type User struct {
    Name string
    Age  int
}

func UpdateAge(u *User, newAge int) {
    u.Age = newAge
}

func main() {
    u := User{Name: "Alice", Age: 25}
    UpdateAge(&u, 30)
    fmt.Println(u.Age) // 30
}
```

```go
type Counter struct {
    Count int
}

func Increment(c *Counter) {
    c.Count++
}

func main() {
    c := &Counter{}
    Increment(c)
    fmt.Println(c.Count) // 1
}
```

---

## Interfaces

```go
type Speaker interface {
    Speak() string
}

type Dog struct {}

func (d Dog) Speak() string {
    return "Woof!"
}

func MakeSpeak(s Speaker) {
    fmt.Println(s.Speak())
}

p := Dog{}
MakeSpeak(p)
```
