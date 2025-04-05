# Rust Generics

## What Are Generics?
Generics allow you to write flexible and reusable functions, types, or data structures. They enable you to write code that can work with different data types without sacrificing performance.

### Syntax
```rust
fn generic_function<T>(x: T) {
    println!("{}");
}
```
- `T` is a placeholder for any data type. The angle brackets (`<>`) denote the usage of generics.

## Using Generics with Structs
```rust
struct Point<T> {
    x: T,
    y: T,
}

let integer_point = Point { x: 5, y: 10 };
let float_point = Point { x: 1.0, y: 4.0 };
```

## Using Generics with Enums
```rust
enum Option<T> {
    Some(T),
    None,
}

let some_number = Some(42);
let some_text = Some("Hello");
```

## Using Generics with Methods
```rust
impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}

let p = Point { x: 5, y: 10 };
println!("x = {}", p.x());
```

## Trait Bounds
- Used to specify that a generic type implements a specific trait.
```rust
fn print<T: std::fmt::Display>(x: T) {
    println!("{}", x);
}
```

## Generic Functions with Multiple Types
```rust
fn mix<T, U>(x: T, y: U) -> (T, U) {
    (x, y)
}

let result = mix(5, "hello");
```

## Performance Considerations
- Rust monomorphizes generic code at compile time.
- This means the compiler generates specific versions of functions for each concrete type, ensuring zero runtime cost.

## Best Practices
- Use generics when you need flexibility.
- Combine with trait bounds for more powerful and safe abstractions.
