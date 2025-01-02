# Basic Concepts

## Variables

* Variables are immutable in rust by default.
* They can be made mutable by using the keyword `mut`
    ```rust
    let x = 7; // Immutable and hence, its value cannot be changed
    let mut y = 6; // Mutable and its value can be changed
    //x = 8; -> Gives an error
    y = 9;
    ```

## Constants

* They are also immutable by nature
* `mut` keyword cannot be used with them
* Declared using the keyword `const`
* The data type must be annotated
* Their value cannot be a value which is computed at run time, i.e. they can be assigmed only with constant expressions or values
    ```rust
    const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
    ```
* Rust’s naming convention for constants is to use all uppercase with underscores between words

## Shadowing

* The same variable name can be used for different variables
* The second variable overshadows the first variable until the scope in which it exists ends or it itself is shadowed
* Example:
    ```rust
    let x = 5;
    let x = 10; // 
    ```
* Differences between `mut` and shadowing:
    * Shadowing doesn't make the variable mutable, instead it creates a new variable of same name
    * Values can be changed using shadowing but the variable still remains immutable
    * Values can be changed using `mut` too, but the new value should be of the same data type
        ```rust
        let mut spaces = "   ";
        spaces = spaces.len();
        ```
        ```bash
        $ cargo run
        Compiling variables v0.1.0 (file:///projects/variables)
        error[E0308]: mismatched types
        --> src/main.rs:3:14
        |
        2 |     let mut spaces = "   ";
        |                      ----- expected due to this value
        3 |     spaces = spaces.len();
        |              ^^^^^^^^^^^^ expected `&str`, found `usize`

        For more information about this error, try `rustc --explain E0308`.
        error: could not compile `variables` (bin "variables") due to 1 previous error
        ```

## Data Types

* Rust is a statically typed language[^1]
* In cases like parsing, the type of data is to be explicitly annotated

There are 2 subsets of data types:
### Scalar Data Types

There are 4 primary scalar types:

1. Integer Data type
    * They are the numbers without fractional part
    * They can be signed or unsigned

		| Length  | Signed | Unsigned |
		|---------|--------|----------|
		| 8-bit   | i8     | u8       |
		| 16-bit  | i16    | u16      |
		| 32-bit  | i32    | u32      |
		| 64-bit  | i64    | u64      |
		| 128-bit | i128   | u128     |
		| arch    | isize  | usize    |
    * The isize and usize types depend on the architecture of the computer your program is running on, which is denoted in the table as “arch”( 64 bits if you’re on a 64-bit architecture and 32 bits if you’re on a 32-bit architecture.)
    * The integers can be represented as following:

		| Number Literals  | Example     |
		|------------------|-------------|
		| Decimal          | 98_222      |
		| Hexadecimal      | 0xff        |
		| Octal            | 0o77        |
		| Binary           | 0b1111_0000 |
		| Byte (u8 only)   | b'A'        |

###  [Compound Types](https://doc.rust-lang.org/book/ch03-02-data-types.html#compound-types)

*Compound types* can group multiple values into one type. Rust has two primitive compound types: tuples and arrays.

1. [The Tuple Type](https://doc.rust-lang.org/book/ch03-02-data-types.html#the-tuple-type)

- A *tuple* is a general way of grouping together a number of values with a variety of types into one compound type. Tuples have a fixed length: once declared, they cannot grow or shrink in size.
	
	```rust
	fn main() { let tup: (i32, f64, u8) = (500, 6.4, 1); }
	```

```rust
	fn main() {
	    let tup = (500, 6.4, 1);
	
	    let (x, y, z) = tup;
	
	    println!("The value of y is: {y}");
	}
```

```rust
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}
```

> `println!("{:#?}", tup); // Pretty-Print` 
```bash
(
    96,
    "MASK",
    9696.9696,
)
```

>`println!("{:?}", tup); // Debug-Print`
```bash
(96, "MASK", 9696.9696)
```
> Works for all collection types (structs too)

2.  [The Array Type](https://doc.rust-lang.org/book/ch03-02-data-types.html#the-array-type)

- Another way to have a collection of multiple values is with an _array_. Unlike a tuple, every element of an array must have the same type. Unlike arrays in some other languages, arrays in Rust have a fixed length.
- You can also initialize an array to contain the same value for each element by specifying the initial value, followed by a semicolon, and then the length of the array in square brackets, as shown here:

```rust
let a = [3; 5];
```
[^1]: Even though rust is a statically typed language, it can still infer the type of data. That is why the compiler did not show an error in the statement `let x = 5`.

3. The String Type

```rust
let mut st1 = String::new();
st1.push('A');
st1.push_str(" Person");
for word in st1.split_whitespace() {
    println!("{}", word);
}
let st2 = st1.replace("A", "Another");
println!("The new string is: \n{}", st2);
```

```rust
let st3 = String::from("a d e  a e r f e t g r t g ");
let mut v1:Vec<char> = st3.chars().collect();
v1.sort();
v1.dedup();
for char in v1 {
    println!("{}", char);
}
```

```rust
let str4 = "random String";
let mut str5 = str4.to_string();
println!("{}", str5); //random String
```

```rust
let byte_arr = str5.as_bytes();
println!("{:?}", byte_arr); // [114, 97, 110, 100, 111, 109, 32, 83, 116, 114, 105, 110, 103]
```

```rust
let str6 = &str5[0..6]; // slicing
println!("{}", str6); // random
```

- The length of the string can be found using `len()` function

```rust
str5.clear(); // Deletes all values in a string
println!("{}", str5); // Empty String
```

```rust
let str6 = String::from("A pack");
let str7 = String::from(" of Wolves");
let str8 = str6 + &str7;
println!("str8 = {}", str8);
println!("str6 = {}", str6);
```

```bash
$ cargo run
   Compiling rust_tutorial v0.1.0 (rust/rust_tutorial)
error[E0382]: borrow of moved value: `str6`
  --> src/main.rs:14:27
   |
10 |     let str6 = String::from("A pack");
   |         ---- move occurs because `str6` has type `String`, which does not implement the `Copy` trait
11 |     let str7 = String::from(" of Wolves");
12 |     let str8 = str6 + &str7;
   |                ---- value moved here
13 |     println!("str8 = {}", str8);
14 |     println!("str6 = {}", str6);
   |                           ^^^^ value borrowed here after move
   |
   = note: this error originates in the macro `$crate::format_args_nl` which comes from the expansion of the macro `println` (in Nightly builds, run with -Z macro-backtrace for more info)
help: consider cloning the value if the performance cost is acceptable
   |
12 |     let str8 = str6.clone() + &str7;
   |                    ++++++++

For more information about this error, try `rustc --explain E0382`.
error: could not compile `rust_tutorial` (bin "rust_tutorial") due to 1 previous error
```

- [More About string types](https://www.youtube.com/watch?v=CpvzeyzgQdw)