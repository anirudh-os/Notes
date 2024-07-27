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
    * Shadowing doesn't make the varible mutable, instead it creates a new variable of same name
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






[^1]: Even though rust is a statically typed language, it can still infer the type of data. That is why the compiler did not show an error in the statement `let x = 5`.