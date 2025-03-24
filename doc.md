

- Setting up your environment and installation to have code on your laptop inorder to run go on your laptop
		Install go on your system and check the version of the go installed on your laptop
		: https://go.dev/doc/install  --- To download golang on your system
		: go version     -- to check the golang version

	- Downloading, get the IDE (Integrated development environment) visual studio code, zed,
		https://www.jetbrains.com/go/
		https://code.visualstudio.com/

	- Open your visual studio code
		create a file main.go   --- This is the entry point of the application, everything start executing and running from main.go
		( A standalone executable belongs to main. Each Go application contains one main. )
		go source code is stored in .go file
		filenames consist of lower case - letters


	Explain packages in go
		- Definition: A package is a collection of Go source files (go files) in the same directory that are compiled together.
		- Purpose: Packages help in organizing code logically (are a way to structure your code) and promoting code reusability.
		- Usage: You import a package when you want to use its exported functions, structs, variables, etc.

		Standard library that has packages ( fmt, math, net/http )
		An application can consist of different packages.

	Modules
		- Definition: A module is a collection of related Go packages that are versioned together as a unit.
		- Purpose: Modules enable dependency management and version control. They allow you to manage your project's dependencies using go.mod and go.sum.
			( go mod init github.com/fullstack )
		- Usage: When you initialize a module using go mod init, it creates a go.mod file where you define the module path and dependencies.



		Identifier
			- An identifier is a name assigned by the user to a program element like a variable, a function, a template, and a struct, etc.  Go is case-sensitive.  Valid identifiers begin with a letter

		Blank identifier
			- The _ itself is a special identifier, called the blank identifier. Like any other identifier, _ can be used in declarations or variable assignments (and any type can be assigned to it).
				However, its value is discarded, so it can no longer be used in the code that follows.

		The basic structure of a Go program
			Programs consist of keywords, constants, variables, operators, types and functions.
			It is also important to know the delimiter and punctuation characters that are a part of Golang.
			The following delimiters are used in a Go program:
			* Parentheses ()
			* Braces {}
			* Brackets []

	continuation on packages

	Import keyword
			- A Go program is created by linking set of packages together, with the import keyword. For example, if you want to import a package say fmt,
			- import "fmt" tells Go that this program needs functions, or other elements from the package fmt, which implements a functionality for formatted IO.
				The package names are enclosed within " "(double quotes).


	Visibility rule
		Packages expose their code objects to code outside of the package according to the following rule enforced by the compiler:
		When the identifier (of a constant, variable, type, function, struct field, …) starts with an uppercase letter, like, fmt.Println  and it is said to be exported.


	Types & Variables
		Variables contain data, and data can be of different data types or types for short. Go is a statically typed language.
		It means the compiler must know the types of all the variables, either because they were explicitly indicated, or because the compiler can infer the type from the code context.
		A type defines the set of values and the set of operations that can take place on those values. Here is an overview of some categories of types:

		- A structured type, which has no real value (yet), has the value nil, which is also the default value for these types. To declare a variable, var keyword is used as:
		- A value that cannot be changed by the program is called a constant. This data can only be of type boolean, number (integer, float, or complex) or string.

		Variables
		A value that can be changed during program execution is called a variable while we have constant that cannnot change
		variable is the keyword

		When a variable is declared, memory in Go is initialized (It means their is a memory address that you get and you can access), which means it contains the default zero or null value depending upon its type automatically.
		For example, 0 for int, 0.0 for float, false for bool, empty string ("") for string, nil for pointer, zero-ed struct, and so on.

		Short form with := assignment operator
			number := 1
			decision := true

			Again the types of number and decision (int and bool) are inferred by the compiler. This is the preferred form, but it can only be used inside functions, not in package scope.
			This operator (:=) effectively makes a new variable; it is also called an initializing declaration. If after the lines above in the same code block, we declare

			Scope of a variable#
				A variable of any type is only known in a certain range of a program, called its scope. In a programming language, there are two main types of scopes:
				* Global scope
				* Local scope

		Initialization of variables (explicit initialization)
		This means you assign a value at the time of declaration

		var x int = 10
		var name string = "Go"

		--- using shorthand (inside the function)
		x := 10
		name := "Go"


		Not Initialization of Variables (Default Initialization)
	    This means you declare the variable but don’t give it any value — Go will automatically assign it the default zero value for its type.

		var x int        // not initialized, so default value is 0
		var name string  // not initialized, so default value is "" (empty string)
		var flag bool    // default is false

		In this case, the variable is not initialized by the programmer, but Go initializes it behind the scenes with a zero value

		“When a variable is declared in Go, memory is allocated, and Go automatically assigns the default zero value to that memory location to ensure safety and predictability.”

		variable notes....
			declare, assign, initialize, and allocate refer to different aspects of working with variables and memory.
			- Declare: Create a variable without assigning it a value.
			- Assign: Set a value to a previously declared variable.
			- Initialize: Declare a variable and assign it a value at the same time.
			- Allocate: Reserve memory for more complex types or for dynamic memory needs.

			1. Declare: Declaring a variable in Go means stating its type and name, but not necessarily giving it a value. This merely reserves a memory spot for the variable.
				A variable can be declared using the `var` keyword. For example, `var x int` declares an integer variable named `x`.

			2. Assign: Assigning a variable means giving a declared variable a value. This is typically done using the `=` operator. For instance,
				if you have declared `var x int` earlier, you could assign it a value with `x = 10`.

			3. Initialize: Initialization refers to the process of declaring a variable and assigning it a value at the same time.
				For instance, `var x int = 10` or `x := 10` (using short declaration) both declare and assign a value to `x`, thus initializing it. This is the typical way variables are created in Go.

			4. Allocate: Allocation refers to reserving a specific amount of memory during the execution of a program,
				usually for more complex types such as slices or structs, or when you need to create a variable dynamically at runtime.
				In Go, you typically use built-in functions like `make()` or `new()` to allocate memory. For example, `x := make([]int, 10)` allocates a slice of integers with a length of 10. `new()` is used to allocate memory and returns a pointer to it, but unlike `make()`, it doesn't initialize the memory.


				BUILTIN TYPES
				Built-in types are those that are built into the language itself, and they don't require any additional libraries to be imported.
					They are ready to use straight out of the box. The built-in types in Go are:

				Boolean types:
				- `bool`: A boolean type that can have the values `true` or `false`.

				Numeric types:
				- `uint8`, `uint16`, `uint32`, `uint64`: Unsigned (non-negative) integers that can be 8, 16, 32, or 64 bits long, respectively.
				- `int8`, `int16`, `int32`, `int64`: Signed integers that can be 8, 16, 32, or 64 bits long.
				- `uint`, `int`, `uintptr`: An unsigned integer, an integer, and a pointer-sized unsigned integer whose size depends on the type of architecture you're compiling for (32 or 64 bits).
				- `float32`, `float64`: A floating point number that can be 32 or 64 bits long.
				- `complex64`, `complex128`: A complex number with float32 or float64 real and imaginary parts.
				- `byte`: An alias for `uint8`.
				- `rune`: An alias for `int32`. It represents a Unicode code point.

				String types:
				- `string`: A sequence of bytes. It's often used to hold text.

				Error type:
				- `error`: A built-in interface type used for representing and manipulating errors.

				REFERENCE TYPES

				- Slices: A slice is a descriptor of an array segment. It consists of a pointer to the array, the length of the segment, and its capacity (the maximum length of the segment).
					If you pass a slice to a function, it will be able to modify the underlying array.

				- Maps: A map is an unordered collection of key-value pairs. Maps in Go are implemented as hash tables and they are references to the underlying data structure.
					If you pass a map to a function, the function can change the map's elements.

				- Channels: Channels are the pipes that connect concurrent goroutines. You can send values into channels from one goroutine and receive those values into another goroutine.
					Like slices and maps, channels are reference types.

				- Pointers: A pointer holds the memory address of a value. Pointers in Go support the "reference semantics" behavior.

				- Interfaces: An interface type is defined by a set of methods. A value of interface type can hold any value that implements those methods.
				``Interface values are a combination of a value and a concrete type. They have reference semantics.

				- Functions: Functions in Go are first-class citizens and can be assigned to variables or passed around just like any other types.
					Functions have reference semantics as well.

				While these types have reference-like behavior, it's worth noting that Go does not have "classes" or "objects" in the traditional sense, and therefore does not have reference types in the way that languages with a class-based object-oriented model do.
				Instead, Go has user-defined types and supports composition and interfaces to provide flexible ways of structuring your code.

				STRUCTS
				Structs: Structs are a way to group together variables of different types.

				------------------------
				other ways we can categorize types
				------------------------

				COMPOSITE TYPES / AGGREGATE TYPES:
				array: A numbered sequence of elements of a specific length.

				slice: A dynamically-sized, flexible view into the elements of an array.

				struct: A composite data type that groups together zero or more values of different types.

				pointer: Holds the memory address of a value.

				function: A sub-routine which is a group of statements that together perform a task.

				interface: Defines a contract for certain behavior (like methods) that the types should have.

				map: An unordered group of elements of one type, called the element type, indexed by a set of unique keys of another type, called the key type.

				channel: A conduit through which you can send and receive values with the channel operator, <-.


				USER DEFINED TYPES:
				User-defined types are types that are defined by the programmer, not the language. They allow you to create complex data structures by COMPOSING together existing types, be they built-in or other user-defined types.

				Here are some examples of user-defined types in Go:

				- STRUCTS: Structs are a way to group together variables of different types. You could define a struct to represent a person, for example, with a name and an age:

				type Person struct {
					Name string
					Age  int
				}

				- INTERFACES: Interfaces define a contract of methods that a type should implement. They are central to Go's type system and enable polymorphic behavior.

				type Shape interface {
					Area() float64
				}

				- ALIASES: You can also define a new type as an alias of an existing one, which can be useful for improving code readability or for encapsulating functionality. For example:

				type IZ int

                var age IZ = 5 

				In this case, `Age` is a new type, but it has the same underlying type as `int`. You can define methods on these user-defined types.

				- FUNCTIONS: In Go, functions are first-class citizens, meaning they can be defined as types and then used as arguments or return values in other functions. For example:

				type BinaryOperation func(a int, b int) int

				In this case, `BinaryOperation` is a function type that takes two `int` parameters and returns an `int`.

				Note that while Go does allow you to define new types in these ways, it does not support classes or inheritance in the way that some other languages do. Instead, it encourages composition and the use of interfaces to define behavior.

			Printing
				We have been using the Println function from the fmt package so far, to print output to console. This package provides us another function, Printf, that prints the output on console but has a different format. It generally uses a format-string as its first argument:

				This format string can contain one or more format-specifiers. Some common format specifiers are:
				* %d specifies format for integral values.
				* %s specifies format for string values.
				* %v specifies the general default format.

                Example: 	// fmt.Printf("What are the nos in this collections %d\n", numbers)

			

		FUNCTION

			- Functions are the basic building blocks of the Go code. 
			- Functions are a kind of data because they are themselves values and have types. 
			- Every program consists of several functions. It is the basic code block. The order in which the functions are written in the program does not matter. 
			- However, for readability, it is better to start with main() and write the functions in a logical order (for example, the calling order).

			- The main purpose of functions is to break a large problem, which requires breaking many code lines into a number of smaller tasks. 
			- Also, the same task can be invoked several times, so a function promotes code reuse. In fact, a good program honors the Don’t Repeat Yourself principle, meaning that the code which performs a certain task may only appear once in the program.

			There are 3 types of functions in Go:
				* Normal functions with an identifier
				* Anonymous or lambda functions
				* Methods
				Any of these can have parameters and return values.
				The definition of all the function parameters and return values together with their types is called the function signature.
			Function is a function in package pack1, and arg1, and so on are the arguments. When a function is invoked, copies of the arguments are made, and these are then passed to the called function.

			Return from a function
			Returning value(s) is done with the keyword return. In fact, every function that returns at least 1 value must end with return

			Pass by value
			function(arg1)

			Pass by reference
			If you want Function to be able to change the value of arg1 itself (in place), you have to pass the memory address of that variable with &; this is call (pass) by reference:
			function(&arg1)

			Reference type like slices, map, interfaces and channels are passed by reference by default


			The defer keyword#
				The defer keyword allows us to postpone the execution of a statement or a function until the end of the enclosing (calling) function. 
				Defer executes something (a function or an expression) when the enclosing function returns. This happens after every return, even when an error occurs in the midst of executing the function, not only a return at the end of the function, but before the. 
				But why after every return? This happens because the return statement itself can be an expression that does something instead of only giving back 1 or more variables. 
				in most cases, it also serves to free up allocated resources. However, keep in mind that a defer-call is function scoped, while a finally-call is block scoped.

				The defer allows us to guarantee that certain clean-up tasks are performed before we return from a function, for example:
				* Closing a file stream
				* Unlocking a locked resource (a mutex)
				* Printing a footer in a report
				* Closing a database connection
				The defer can be helpful to keep the code cleaner and often shorter.



			Array

			Array in go

				- We start by examining data-structures that contain a number of items, called collections, such as arrays (slices) and maps. 
				- The array-type indicated by the [] notation is well-known in almost every programming language as the basic workhorse in applications.
				- The Go array is very much the same but has a few peculiarities. 
				- Go has the slice type. This is an abstraction built on top of Go’s array type. So to understand slices, we must first understand arrays. 
				- Arrays have their place, but they are a bit inflexible. Therefore, you don’t see them too often in Go code. Slices, though, are everywhere, and they are built on arrays to provide greater power and convenience.

				- An array is a numbered and fixed-length sequence of data items (elements) of the same type (it is a homogeneous data structure). 
				- This type can be anything from primitive types like integers or strings to self-defined types. The length must be a constant expression, that must evaluate to a non-negative integer value. 
				- It is part of the type of the array, so arrays declared as [5]int and [10]int differ in type. The items can be accessed and changed through their index (their position). The index starts from 0, so the 1st element has index 0, the 2nd index 1.
				- The number of items, also called the length (called len) or size of the array, is fixed and must be given when declaring the array (length has to be determined at compile time in order to allocate the memory).

				var identifier [len]type

				var arr1 [5]int

				Because of the index, a natural way to loop over an array is to use the for-construct:
				* for initializing the items of the array
				* for printing the values or in general
				* for processing each item in succession


				Array literals#
				When the values (or some of them) of the items are known beforehand, a simpler initialization exists using the { , ,} notation called array literals (or constructors) instead of initializing every item in the [ ]= way. Let’s see some variants.
				1st variant
				Specify explicitly the size n of the array with [n]. For example:

				var arrAge = [6]int{28, 50, 15, 22, 17, 18}


				A slice is a reference to a contiguous segment (section) of an array (which we will call the underlying array, and which is usually anonymous), so a slice is a reference type.
				This section can be the entire array or a subset of the items indicated by a start and an end index (the item at the end index is not included in the slice). Slices provide a dynamic window to the underlying array.

				A slice in memory is a structure with 3 fields:
				* a pointer to the underlying array
				* the length of the slice
				* the capacity of the slice
				Slices are indexable and have a length given by the len() function. The slice-index of a given item can be less than the index of the same element in the underlying array. 
				Unlike an array, the length of a slice can change during the execution of the code, minimally 0 and maximally the length of the underlying array, which means a slice is a variable-length array.
				The built-in capacity function cap() of a slice is a measure of how long a slice can become. It is the length of the slice + the length of the array beyond the slice. 
				If s is a slice, cap is the size of the array from s[0] to the end of the array. A slice’s length can never exceed its capacity, so the following statement is always true for a slice s:



				Multiple slices can share data if they represent pieces of the same array, but multiple arrays can never share data. 
				A slice, therefore, shares storage with its array and with other slices of the same array. In contrast, distinct arrays always represent distinct storage. Arrays are in fact building blocks for slices.
				Because slices are references, they don’t use up additional memory and they are more efficient to use than arrays. That’s the reason why they are used much more than arrays in Go-code. The format of the declaration is:

				var identifier []type     // no length is specified


				loop in slice — for range
				seasons := []string{"Spring","Summer","Autumn","Winter"}
				for ix, season := range seasons {
				fmt.Printf("Season %d is: %s\n", ix, season)
				}

				var season string
				for _, season = range seasons {
				fmt.Printf("%s\n", season)
				}

			Maps are a special kind of data structure: an unordered collection of pairs of items, where one element of the pair is the key, and the other element, associated with the key, is the data or the value. Hence they are also called associative arrays or dictionaries. 
			They are ideal for looking up values, and given the key, the corresponding value can be retrieved very quickly. This structure exists in many other programming languages under other names such as Dictionary (dict in Python), hash, HashTable and so on

			A map is a reference type and declared generally as: 
			
			var map1 map[keytype]valuetype

			var map1 map[string]int

			The length of the map doesn’t have to be known at the declaration, which means a map can grow dynamically. The value of an uninitialized map is nil. The key type can be any type for which the operations == and != are defined, like string, int, and float. 
			For arrays and structs, Go defines the equality operations, provided that they are composed of elements for which these operations are defined using element-by-element comparison. So arrays, structs, pointers, and interface types can be used as key type, but slices cannot because equality is not defined for them. The value type can be any type.
			Maps are cheap to pass to a function because only a reference is passed (so 4 bytes on a 32-bit machine, 8 bytes on a 64-bit machine, no matter how much data they hold). Looking up a value in a map by key is fast, much faster than a linear search, but still around 100x slower than direct indexing in an array or slice. So, if performance is very important try to solve the problem with slices.



			Introduction to Struct
			This lesson introduces structs, addressing rudimentary concepts such as declaration and memory allocation.
			Go supports user-defined or custom types in the form of alias types or structs. A struct tries to represent a real-world entity with its properties. Structs are composite types to use when you want to define a type that consists of several properties each having their type and value, grouping pieces of data together. Then, one can access that data as if it were part of a single entity.
			Structs are value types and are constructed with the new function. The component pieces of data that constitute the struct type are called fields. A field has a type and a name. Field names within a struct must be unique.
	
			However, because Go does not have the concept of a class, the struct type has a much more important place in Go.
			Definition of a struct
			The general format of the definition of a struct is as follows:
			type identifier struct {
			field1 type1
			field2 type2
			...
			}


			A Go method is a function that acts on a variable of a certain type, called the receiver. Therefore, a method is a special kind of function.
			Note: A method acting on a variable in Go is similar to the object of a class calling its function in other OO languages, using a . selector, e.g., object.function().

			The receiver type can be (almost) anything, not only a struct type. Any type can have methods, even a function type or alias types for int, bool, string, or array. However, the receiver cannot be an interface type since an interface is an abstract definition and a method is the implementation. Trying to do so generates the compiler error: invalid receiver type.
			Lastly, a method cannot be a pointer type, but it can be a pointer to any of the allowed types. The combination of a (struct) type and its methods is the Go equivalent of a class in OO. One important difference is that the code for the type and the methods binding to it are not grouped together. They can exist in different source files; the only requirement is that they have to be in the same package.
			The collection of all the methods on a given type T (or *T) is called the method set of T (or *T).
			Methods are functions, so again, there is no method overloading, which means for a given type, there is only one method with a given name. However, based on the receiver type, there is overloading. A method with the same name can exist on two or more different receiver types, e.g., this is allowed in the same package:

			Differences between a function and a method
			A function has the variable as a parameter:
			Function1(recv)
            
			A method is called on the variable:
			recv.Method1()
			A method can change the values (or the state) of the receiver variable provided this is a pointer, just as is the case with functions (a function can also change the state of its parameter when this is passed as a pointer: call by reference).

			The receiver must have an explicit name, and this name must be used in the method. receiver-type is called the (receiver) base type; this type must be declared within the same package as all of its methods. In Go, the methods attached to a (receiver) type are not written inside of the structure, as is the case with classes; the coupling is much loose: the receiver establishes the association between method and type.
			Methods are not mixed with the data definition (the structs). They are orthogonal to types; representation (data) and behavior (methods) are independent.

			Pointer or value as a receiver#
			The recv is most often a pointer to the receiver-type for performance reasons (because we don’t make a copy of the value, as would be the case with call by value); this is especially true when the receiver type is a struct. Define the method on a pointer type if you need the method to modify the data the receiver points to. Otherwise, it is often cleaner to define the method on a normal value type.


codes 