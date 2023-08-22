# A tour of Rust features and its dejavu


### Zero-Cost Abstractions. 

Rust borrows from C++ and this principle can be summarized with the following phrase:
- What you don't use, you don't pay for.
- What you do use, you could not get any other hand coded better. 
The high level abstractions like generics and collections (*generics, iterators, templates, collections, classes*) should not impose any runtime overhead or performance penalties compared to code using low level abstractions like for loops, counters, if/else, row pointers.
_See more : [Rust vs Java generic](LAN_rust_vs_java_generic.md)_


C++ example:

Dummy version: less readable and more prone to errors
```C++
int main(){
	std::vector<int> numbers = {5, 2, 8, 1, 3};
	int maxElement = numbers[0];
	for (size_t i = 1; i < numbers.size(); i ++){
		if (numbers[i] > maxElement){
			maxElement = numbers[i];
		}	
	}
	std::cout << "Maximum element: " << maxElement << std::endl;
	return 0; 
}
```

Using iterator abstraction: 
```C++
int main(){
	std::vector<int> numbers = {5, 2, 8, 1, 3}
	auto maxElement = std::max_element(numbers.begin(), numbers.end());
	std::cout << "Max element: " << *maxElement << std::endl;
	return 0;
}
```

Rust: 
```rust
fn main(){
	let numbers = vec![5, 2, 8, 1, 3];
	let max_element = numbers.iter().max();
	match max_element {
		Some(&max) => println!("Maximum element: {}", max_element),
		None => println!("The vector is empty."),
	}
}
```

Python: 
In python, iterators are not zero cost abstraction. Python requires additional runtime check to ensure the integrity of the iteration process because collections can change in size or structure during iteration. 

### Ownership

Ownership is one of rust's most fundamental features. Ownership is actually based on the **Resource Acquisition Is Initialization** design pattern in  C++ (RAII). The RAII states that:
- allocated memory
- file handles
- database connections
should be tied to object lifetimes. when object is created, it acquires resources  and when the object is destroyed, those resources are released. 

Rust integrated RAII directly in to the language, so you dont have to remember to use the pattern. The compiler does it automatically for you by following Ownership Rules. 
Rust further builds on top of the Ownership Rules by combining them with the Borrowing Rule. The Borrowing Rule states that, at any given time, you can either have one mutable reference or any number of immutable references. 

By enforcing that rule, rust prevents bugs called data race. 

### Functional 

ADT : Algebraic Data Types. This concept is commonly found in functional languages like Haskel.. This allow us to create composite type using Sum Types and Product Types

- Sum types (enum)
- Product types similar to Struct class. 

```rust
enum Employee {
	Manager { name: String, subordinates: Vec<Box<Employee>>},
	Worker { name: String, manager: String
	},
}

let employee = Employee::Worker{ name: "Brian".to_string(), manager: "His wife".to_string()};
match employee {
	Employee::Manager {name, subodinates}  => print(
	" "),
	Employee::Worker {name, manager} => println!(" ... "),
}
```

Rust implements ADT through enum and struct, but unlike Haskell, the Rust'ADT is imperative style.
### Polymorphism

Some languages implements Polymorphism through inheritance, but rust takes a different approach. In Rust Poly is implemented with Traits and Generics. - - 

- Traits define a set of functions and methods that types can implement, similar to interface in other languages.
- Generic are the other hand enables us to write code that is abstracted over type. This feature can be found in almost any language.

 The traits system in Rust hast its roots in Haskell's type classes which provide shared behaviors for type but Rust builds on top of the concept of type classes by incorporating ownership, borrowing and lifetimes into the traits system. 
 
 Rust are also supports Dynamic dispatch with Traits Objects that allow you to treat different types that implement the same trait as interchangeable. For example, you can create a Vector of Rectangle and Circle.
 ```Rust
 let shapes: Vec<Box<dyn Shape>> = vec![Box::new(rectangle), Box::new(circle)]
```
 
The Traits System in Rust has several advantages over classical inheritance:

[1]**Flexibility and Composition**:  Its allows for more flexible code design and composition. Multiple types can independently implement the same trait enabling flexible composition without relying on strict inheritance hierarchies. 

[2] **Non-invasive and Extensive**: Behavior to be added to types without modifying their original implementation or inheritance hierarchy. 

[3] **No Fragile of Base Class Problem**.

[4] **Static Dispatch and Performance.** 


### Async Programming

Just like Js, the async/await syntax is a sugar syntactic for working with Futures which are similar to Promises. There are few differences:
- In Rust, Futures are designed to be lazy. -> can be scheduled, composed and combined with other Futures without any overhead. And Rust provides true parallelism
- In Js, Futures are Eager and is single threaded. Just an illusion of parallelism.


### Meta programming

Rust support two approach to meta-programming: Procedural Macros and Compile-Time Code Execution. Some of the languages that have influenced the design and features of Rust Meta Programming
- C/C++. Rust's macros are more powerful and flexible compare to C++ and C++ supports a form of metaprogramming called template metaprogramming, where computations and code generation occur at compile time using template specialization and type traits. Rust's type system and associated constants/types feature share some similarities with C++ template metaprogramming.
- Lisp, to be honest, iam not known well about Lisp, but there are alot topics about the simmilar of Rust meta-programming vs Lisp design. 

**In summary**: Rust has emerged as a beloved language among thousands of engineers, both as a hobby and in professional settings. While the individual features provided by Rust may not be entirely novel, it is the unique way in which Rust combines these features with its safety and ownership model that sets it apart. This innovative approach is a key factor in Rust's growing popularity as we enter the year 2023.
