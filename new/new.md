# Go Development Setup Guide

## 🚀 Setting Up Your Environment and Installation

To run Go on your system, follow the steps below:

### ✅ Install Go on Your System
- Download and install Go: [https://go.dev/doc/install](https://go.dev/doc/install)
- Verify installation:
  ```bash
  go version
  ```

---

### 💻 Install an IDE (Integrated Development Environment)
Choose any of the following IDEs for a better coding experience:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Zed](https://zed.dev/)
- [GoLand by JetBrains (Paid)](https://www.jetbrains.com/go/)

---

### 📂 Creating Your First Go File
1. Open your preferred IDE (e.g., Visual Studio Code).
2. Create a new file named `main.go`.

> 🔹 `main.go` is the entry point of a Go application. The Go runtime starts executing your code from the `main` package and the `main()` function.

- Go source code files have a `.go` extension.
- Filenames typically use lowercase letters.

---

## 📦 Understanding Packages in Go

### What is a Package?
- A **package** is a collection of Go source files in the same directory that are compiled together.
- Packages help organize your code logically and promote **code reusability**.

### Using Packages
- You **import** packages to use their exported functions, structs, and variables.
- Example:
  ```go
  import "fmt"
  ```

### Common Standard Library Packages
- `fmt` - Formatting and printing
- `math` - Mathematical functions
- `net/http` - HTTP client and server

> 🔸 A Go application can consist of multiple packages.


### Import Keyword
- A Go program is created by **linking packages together** using the `import` keyword.
- Example:
  ```go
  import "fmt"
  ```
- This tells Go that the program needs functions or other elements from the `fmt` package (which is used for formatted I/O).

### Visibility Rule
- Packages expose their code objects to other packages based on identifier naming:
  - If an identifier (constant, variable, function, etc.) **starts with an uppercase letter**, it is **exported** and visible outside the package.
  - Example: `fmt.Println`

---

## 📁 Modules in Go

### What is a Module?
- A **module** is a collection of related Go packages versioned together.
- It provides **dependency management** and **version control**.
- When there is a valid **go.mod file** in the root of your project directory, your project is a module

### Initializing a project as a Module
- To initialize a module, use:
  ```bash
  go mod init github.com/fullstack
  ```

### Module Files
- `go.mod` — defines your module path and dependencies.
- `go.sum` — maintains the checksums of dependencies for verification.
- `go get` - to get dependency
- `go mod tidy` - to install included dependency
---

## 🆔 Identifiers in Go

### What is an Identifier?
- An **identifier** is a name assigned by the user to a program element like a variable, a function, a template, or a struct.
- Go is **case-sensitive**. Valid identifiers begin with a letter.

### Blank Identifier
- The `_` (underscore) is a **special identifier**, called the **blank identifier**.
- Like any other identifier, `_` can be used in declarations or variable assignments (any type can be assigned to it).
- However, its value is **discarded** and cannot be used in the code that follows.

---

## 🏗️ Basic Structure of a Go Program
Programs consist of **keywords**, **constants**, **variables**, **operators**, **types**, and **functions**.

### Common Delimiters in Go:
- Parentheses `()`
- Braces `{}`
- Brackets `[]`


## 🔤 Types & Variables in Go

### Overview
- Variables hold data, and data belongs to different **data types** (or just **types**).
- Go is a **statically typed language**, meaning the compiler must know the type of every variable.

### Type Definition
- A **type** defines the set of values and operations that can be applied to those values.
- A **structured type** (e.g., pointer, slice, map) has a default value of `nil`.

### Declaring Variables
- Use the `var` keyword:
  ```go
  var x int = 10
  var name string = "Go"
  ```

### Constants
- A **constant** is a value that **cannot be changed** during program execution.
- Constants can be of type: `boolean`, `number` (integer, float, complex), or `string`.

### Variables
- A **variable** is a value that **can be changed** during program execution.
- When declared, a variable is **automatically initialized** to a default zero value:
  - `0` for `int`
  - `0.0` for `float`
  - `false` for `bool`
  - `""` for `string`
  - `nil` for pointer, zero-ed struct, etc.

### Short Variable Declaration (Inside Functions Only)
```go
number := 1
decision := true
```
- The type is inferred by the compiler (`int`, `bool`, etc.).
- This form is also known as **initializing declaration** and is **only allowed inside functions**.

### Variable Scope
- The **scope** of a variable determines where it can be accessed.
  - **Global scope**: accessible throughout the program.
  - **Local scope**: accessible only within a specific function or block.

### Explicit Initialization
- Variables can be assigned values at the time of declaration:
  ```go
  var x int = 10
  var name string = "Go"
  ```

---

### Using Shorthand (Inside a Function)
```go
x := 10
name := "Go"
```

### Not Initialization of Variables (Default Initialization)
This means you declare the variable but don’t give it any value — Go will automatically assign it the default zero value for its type.

```go
var x int        // not initialized, so default value is 0
var name string  // not initialized, so default value is "" (empty string)
var flag bool    // default is false
```

> In this case, the variable is not initialized by the programmer, but Go initializes it behind the scenes with a zero value.

> “When a variable is declared in Go, memory is allocated, and Go automatically assigns the default zero value to that memory location to ensure safety and predictability.”

---

### Variable Notes
Declare, assign, initialize, and allocate refer to different aspects of working with variables and memory:

- **Declare**: Create a variable without assigning it a value.
- **Assign**: Set a value to a previously declared variable.
- **Initialize**: Declare a variable and assign it a value at the same time.
- **Allocate**: Reserve memory for more complex types or for dynamic memory needs.

#### 1. Declare
```go
var x int // declares an integer variable named x
```

#### 2. Assign
```go
x = 10 // assigns a value to x
```

#### 3. Initialize
```go
var x int = 10
x := 10 // short declaration
```

#### 4. Allocate
```go
x := make([]int, 10) // allocates a slice of integers
ptr := new(int)      // allocates memory and returns a pointer
```

---

### Built-in Types

#### Boolean types:
- `bool`: A boolean value — `true` or `false`.

#### Numeric types:
- Unsigned: `uint8`, `uint16`, `uint32`, `uint64`
- Signed: `int8`, `int16`, `int32`, `int64`
- Architecture-dependent: `uint`, `int`, `uintptr`
- Floating point: `float32`, `float64`
- Complex: `complex64`, `complex128`
- Aliases: `byte` (alias for `uint8`), `rune` (alias for `int32`)

#### String types:
- `string`: A sequence of bytes used to represent text.

#### Error type:
- `error`: A built-in interface for error handling.

---

### Reference Types

- **Slices**: Dynamic view into an array.
- **Maps**: Key-value pairs (hash tables).
- **Channels**: Communication between goroutines.
- **Pointers**: Hold memory addresses.
- **Interfaces**: Define behavior contracts.
- **Functions**: First-class citizens in Go (assignable, passable).

---

### Structs
- A way to group multiple variables (fields) of different types.

---

### Other Type Categories

#### Composite / Aggregate Types:
- **Array**: Fixed-length collection of elements.
- **Slice**: Flexible, dynamic collection.
- **Struct**: Group of mixed-type fields.
- **Pointer**: Memory address holder.
- **Function**: Task-performing subroutine.
- **Interface**: Contract of behavior (methods).
- **Map**: Unordered collection of key-value pairs.
- **Channel**: Concurrent communication pipeline.



## USER DEFINED TYPES:
User-defined types are types that are defined by the programmer, not the language. They allow you to create complex data structures by COMPOSING together existing types, be they built-in or other user-defined types.

Here are some examples of user-defined types in Go:

- **STRUCTS:** Structs are a way to group together variables of different types. You could define a struct to represent a person, for example, with a name and an age:

```go
type Person struct {
	Name string
	Age  int
}
```

- **INTERFACES:** Interfaces define a contract of methods that a type should implement. They are central to Go's type system and enable polymorphic behavior.

```go
type Shape interface {
	Area() float64
}
```

- **ALIASES:** You can also define a new type as an alias of an existing one, which can be useful for improving code readability or for encapsulating functionality. For example:

```go
type IZ int
var age IZ = 5
```

In this case, `Age` is a new type, but it has the same underlying type as `int`. You can define methods on these user-defined types.

- **FUNCTIONS:** In Go, functions are first-class citizens, meaning they can be defined as types and then used as arguments or return values in other functions. For example:

```go
type BinaryOperation func(a int, b int) int
```

In this case, `BinaryOperation` is a function type that takes two `int` parameters and returns an `int`.

Note that while Go does allow you to define new types in these ways, it does not support classes or inheritance in the way that some other languages do. Instead, it encourages composition and the use of interfaces to define behavior.

## PRINTING
We have been using the `Println` function from the `fmt` package so far, to print output to console. This package provides us another function, `Printf`, that prints the output on console but has a different format. It generally uses a format-string as its first argument:

This format string can contain one or more format-specifiers. Some common format specifiers are:
- `%d` specifies format for integral values.
- `%s` specifies format for string values.
- `%v` specifies the general default format.

**Example:**
```go
fmt.Printf("What are the nos in this collections %d
", numbers)
```


## FUNCTIONS

- Functions are the basic building blocks of the Go code.
- Functions are a kind of data because they are themselves values and have types.
- Every program consists of several functions. It is the basic code block. The order in which the functions are written in the program does not matter.
- However, for readability, it is better to start with `main()` and write the functions in a logical order (for example, the calling order).

- The main purpose of functions is to break a large problem, which requires breaking many code lines into a number of smaller tasks.
- Also, the same task can be invoked several times, so a function promotes code reuse. In fact, a good program honors the Don’t Repeat Yourself principle, meaning that the code which performs a certain task may only appear once in the program.

There are 3 types of functions in Go:
- Normal functions with an identifier
- Anonymous or lambda functions
- Methods

Any of these can have parameters and return values. The definition of all the function parameters and return values together with their types is called the function signature.

Function is a function in package `pack1,` and `arg1,` and so on are the arguments. When a function is invoked, copies of the arguments are made, and these are then passed to the called function.

### Return from a function
Returning value(s) is done with the keyword `return`. Every function that returns at least 1 value must end with `return`.

### Pass by value
```go
function(arg1)
```

### Pass by reference
If you want a function to be able to change the value of `arg1` itself (in place), you have to pass the memory address of that variable with `&`; this is call (pass) by reference:
```go
function(&arg1)
```

Reference types like slices, maps, interfaces, and channels are passed by reference by default.

## DEFER
The `defer` keyword allows us to postpone the execution of a statement or a function until the end of the enclosing (calling) function.

Defer executes something (a function or an expression) when the enclosing function returns. This happens after every return, even when an error occurs during the execution of the function.

Why after every return? Because the return statement itself can be an expression that does something instead of only giving back 1 or more variables.

In most cases, `defer` serves to free up allocated resources. However, keep in mind that a `defer` call is function scoped.

### Use Cases of Defer:
- Closing a file stream
- Unlocking a locked resource (a mutex)
- Printing a footer in a report
- Closing a database connection

The `defer` can be helpful to keep the code cleaner and often shorter.

## ARRAY

### Arrays in Go
- Collections like arrays (slices) and maps store multiple values.
- The Go array is fixed-length and homogeneous. The length must be a constant and is part of the array type.
- Arrays are not commonly used directly in Go as slices provide more flexibility.

```go
var arr1 [5]int
```

Use for loops to iterate over arrays.

### Array Literals
```go
var arrAge = [6]int{28, 50, 15, 22, 17, 18}
```

## SLICES

- A slice is a reference to a contiguous segment of an array.
- Slices have 3 fields: pointer to array, length, and capacity.
- Slices are dynamic and used more than arrays in Go.

**Slice format:**
```go
var identifier []type
```

**Loop in slice — for range:**
```go
seasons := []string{"Spring","Summer","Autumn","Winter"}
for ix, season := range seasons {
    fmt.Printf("Season %d is: %s\n", ix, season)
}
```


## MAPS

- Maps are unordered collections of key-value pairs.
- Declared as:
```go
var map1 map[keytype]valuetype
var map1 map[string]int
```
- Keys must support `==` and `!=`. Values can be any type.
- Maps grow dynamically and are passed by reference.



## Introduction to Struct

This lesson introduces structs, addressing rudimentary concepts such as declaration and memory allocation.

Go supports user-defined or custom types in the form of alias types or structs. A struct tries to represent a real-world entity with its properties. Structs are composite types to use when you want to define a type that consists of several properties each having their type and value, grouping pieces of data together. Then, one can access that data as if it were part of a single entity.

Structs are value types and are constructed with the `new` function. The component pieces of data that constitute the struct type are called fields. A field has a type and a name. Field names within a struct must be unique.

However, because Go does not have the concept of a class, the struct type has a much more important place in Go.

### Definition of a struct
The general format of the definition of a struct is as follows:

```go
type identifier struct {
    field1 type1
    field2 type2
    ...
}
```

### Methods in Go

A Go method is a function that acts on a variable of a certain type, called the receiver. Therefore, a method is a special kind of function.

> Note: A method acting on a variable in Go is similar to the object of a class calling its function in other OO languages, using a `.` selector, e.g., `object.function()`.

The receiver type can be (almost) anything, not only a struct type. Any type can have methods, even a function type or alias types for int, bool, string, or array. However, the receiver cannot be an interface type since an interface is an abstract definition and a method is the implementation.

Lastly, a method cannot be a pointer type, but it can be a pointer to any of the allowed types. The combination of a (struct) type and its methods is the Go equivalent of a class in OO. One important difference is that the code for the type and the methods binding to it are not grouped together. They can exist in different source files; the only requirement is that they have to be in the same package.

The collection of all the methods on a given type `T` (or `*T`) is called the method set of `T` (or `*T`).

### Differences between a function and a method

- A function has the variable as a parameter:
  ```go
  Function1(recv)
  ```

- A method is called on the variable:
  ```go
  recv.Method1()
  ```

A method can change the values (or the state) of the receiver variable provided this is a pointer, just as is the case with functions (a function can also change the state of its parameter when this is passed as a pointer: call by reference).

The receiver must have an explicit name, and this name must be used in the method. `receiver-type` is called the (receiver) base type; this type must be declared within the same package as all of its methods. In Go, the methods attached to a (receiver) type are not written inside of the structure, as is the case with classes; the coupling is much loose: the receiver establishes the association between method and type.

Methods are not mixed with the data definition (the structs). They are orthogonal to types; representation (data) and behavior (methods) are independent.

### Pointer or value as a receiver

The `recv` is most often a pointer to the receiver-type for performance reasons (because we don’t make a copy of the value, as would be the case with call by value); this is especially true when the receiver type is a struct. Define the method on a pointer type if you need the method to modify the data the receiver points to. Otherwise, it is often cleaner to define the method on a normal value type.