/*
	define variables: two of variable declaration 
	what is global and local variable, ...Talk briefly about pointers

	// var myLocation string = "Nigeria, Lagos"
	p := "Johnny"
	fmt.Println(&p)
	fmt.Printf("Deferencing the variable value %v\n", p)
	fmt.Println(myLocation)


	// Pointer 

	What is a pointer?
	A pointer holds the memory address of a variable. Go uses pointers for reference-based programming and optimization.

	Why use pointers?
	Avoid copying large structs.
	Modify values inside functions.
	Efficient memory usage.


	var x int = 10
	var p *int = &x

	var isLoggedIn bool = true
	if isLoggedIn {
		fmt.Println("Welcome back!")
	}


	



*/


// Function

/*

	func add(a int, b int) int {
    	return a + b
	}

	func calculateTax(price float64) float64 {
      return price * 0.15
	}

	tax := calculateTax(1000)
	fmt.Println("Tax:", tax)


*/



// Arrays
/* 

“an array in Go is a value type”, it means that arrays are copied entirely when they are assigned to another variable or passed to a function. 
This is different from reference types like slices, maps, or pointers, where only the reference (memory address) is passed around, not the actual data.

A value type in Go is a type where assignments or function calls create a copy of the data. So, any changes made to the copy do not affect the original.

    var numbers [3]int = [3]int{1,2,3}
	var numbers [3]int
	fmt.Printf("What are the nos in this collections %d\n", numbers)

----------------------------------

	func changeArray(arr [3]int) {
		arr[0] = 99
		fmt.Println("Inside function:", arr)
	}

	func main() {
		original := [3]int{1, 2, 3}
		changeArray(original)
		fmt.Println("Outside function:", original)
	}

----------------------------------------------
	Contrast with Slices

	func changeSlice(s []int) {
		s[0] = 99
		fmt.Println("Inside function:", s)
	}

	func main() {
		original := []int{1, 2, 3}
		changeSlice(original)
		fmt.Println("Outside function:", original)
	}



*/

// Slices
/*

	A slice is a flexible, dynamic-sized view into an array.

	A slice has:
	Pointer to underlying array
	Length
	Capacity


	fruits := []string{"apple", "banana", "cherry"}

	users := []string{"Alice", "Bob", "Charlie"}
	users = append(users, "Diana")
	fmt.Println("User list:", users)

	-------------------------------
	modifying the original data

	numbers := []int{1, 2, 3, 4}
	sub := numbers[1:3] // [2,3]
	sub[0] = 99         // affects original slice
	fmt.Println(numbers) // [1, 99, 3, 4]



*/

// Map
/*
	person := map[string]string{"name": "Alice", "city": "Lagos"}



	var getUserProfile map[int]string
	fmt.Println(getUserProfile)

	userProfile := map[string]string{
		"name": "John",
		"email": "john@example.com",
	}
	// fmt.Println("Name:", userProfile["name"])
	fmt.Println("Name:", userProfile)

*/



// struct examples to use
/*

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

------------------------------------
Pointers: You want to modify data directly or pass large structs efficiently
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

----------------------------------

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

*/



// Interface 
/*

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

---------------------------------------

*/