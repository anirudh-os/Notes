## Enums and Option

### What is an Enum?
- An **enum** (short for enumeration) allows defining a type by enumerating its possible values.
- Useful for representing a value that could be one of several variants.

### Defining an Enum
```rust
enum IpAddrKind {
    V4,
    V6,
}
```
- `IpAddrKind` is an enum with two variants: `V4` and `V6`.
- Unlike structs, enums group related values under one type.

### Using an Enum
```rust
fn route(ip_kind: IpAddrKind) {
    // function logic
}

let four = IpAddrKind::V4;
let six = IpAddrKind::V6;

route(four);
route(six);
```
- Enum variants are namespaced under the enum's name.
- Enums can be used as function parameters.

### Enum with Data
```rust
enum IpAddr {
    V4(String),
    V6(String),
}

let home = IpAddr::V4(String::from("127.0.0.1"));
let loopback = IpAddr::V6(String::from("::1"));
```
- Variants can hold associated data.
- Eliminates the need for separate structs for different variants.

### Enum with Multiple Data Types
```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```
- Enums can hold different data types within their variants.
- This makes them more flexible than traditional structs.

### Implementing Methods for Enums
```rust
impl Message {
    fn call(&self) {
        // method logic
    }
}

let msg = Message::Write(String::from("hello"));
msg.call();
```
- `impl` can be used to define methods for enums.

### The `Option` Enum
- Rust has a built-in `Option<T>` enum to handle the concept of a value being present or absent.
```rust
enum Option<T> {
    Some(T),
    None,
}
```
- `Option<T>` is used to avoid null references.
- Example usage:
```rust
let some_number = Some(5);
let some_string = Some("hello");
let absent_number: Option<i32> = None;
```
- `Option<T>` is commonly used with pattern matching to safely handle missing values.

### Advantages of Enums
- More expressive than structs for certain use cases.
- Variants can hold different types of data.
- Useful in pattern matching (covered in later sections).
