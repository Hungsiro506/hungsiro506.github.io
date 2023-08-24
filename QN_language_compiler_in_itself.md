### Writing a compiler in its own language

A compiler is a program that translates source code written in one programming language into machine code or another language. It is common for a compiler to be written in its own language:
- C++ compilers written in C ++
- Go runtime written in Go
- Rustc is written in Rust
- Javac is itself written in Java. 

However, how is it even possible that the first C++ compiler be written in C++?

The code that makes up the compiler needs to be compiled too, and thus the first C++ compiler couldn't have been written in C++, could it?

Yes, It's possible for compiler to be written in its own languages, but it would require a **bootstrapping process**. The process would involve creating an initial version of the compiler in another language, such as C or assembly, and then using that initial version to compile the source code of the compiler written in its own language. Once the compiler is successfully compiled, it can then be used to compile future versions of itself.It's important to note that this bootstrapping process is not trivial and requires a great deal of expertise and effort. It's also important to note that the initial version of the compiler written in another language is called a "**seed compiler**"

- The very first C++ compiler is a "C with Classes"-to-C preprocessor.  That preprocessor translated "C with Classes" constructs (such as classes and constructors) into C. Then you use "C with Classes" to write a C++ compiler. 
- The original Rustc is written in OCaml.


### But ... Why ? 
The second question should be: Why do programming languages tent to be written in itself ? 
- Simplicity and Consistency: Implementing a compiler in the same language as the one it compiles provides a consistent development environment. It allows developers to work with a single language and its associated tools, libraries, and ecosystem, reducing the need to switch between different languages and tools. You wont be broken by someone else change. 

- Dog-fooding: Using its own will create a feedback loop where the language and its compiler can be iteratively refined together. 
