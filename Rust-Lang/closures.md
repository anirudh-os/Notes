# Rust Closures

## What are Closures?
Closures are anonymous functions you can save in a variable or pass as arguments to other functions. You can create closures in Rust using the following syntax:

```rust
let closure_name = |param1, param2| { body };
```

Closures are different from functions because they can capture variables from their environment.

### Example
```rust
let add = |a, b| a + b;
println!("Sum: {}", add(2, 3));
```

## Characteristics of Closures
1. **Anonymous:** Closures do not have a name.
2. **Environment Capture:** Closures can capture variables from the environment where they are defined.
3. **Type Inference:** The compiler can often infer parameter and return types.
4. **Flexible:** Closures can be stored in variables, passed as arguments, or returned from functions.
5. **Traits:** Closures implement one of three traits (`Fn`, `FnMut`, `FnOnce`) based on how they capture variables.

## Environment Capture
Closures automatically capture variables from their environment, depending on how the closure is used. There are three ways closures can capture variables:

1. **Borrowing Immutably:** `&T`
2. **Borrowing Mutably:** `&mut T`
3. **Taking Ownership:** `T`

### Example of Environment Capture
```rust
let x = 10;
let print_x = || println!("x: {}", x);
print_x();
```

## The `move` Keyword
The `move` keyword forces the closure to take ownership of the variables it uses from its environment.

### Example: Using `move`
```rust
let s = String::from("Hello");
let closure = move || println!("{}", s);
closure();
// `s` is no longer accessible here because it was moved into the closure.
```

### Why Use `move`?
- Required when the closure is used in a thread or returned from a function.
- Ensures that the closure owns the data, making it valid to use after the environment is gone.

## Fn Traits
Depending on how they capture variables, closures implement one of the following traits:
- `Fn`: Immutable borrow of captured values.
- `FnMut`: Mutable borrow of captured values.
- `FnOnce`: Takes ownership of captured values.

### Example: Different Traits
```rust
fn call<F: Fn()>(f: F) {
    f();
}

let name = String::from("Alice");
let print_name = || println!("Hello, {}!", name);
call(print_name);
```

## Returning Closures
Returning a closure from a function requires using `impl Fn` or boxing:

```rust
fn get_closure() -> impl Fn(i32) -> i32 {
    |x| x * 2
}
```

Alternatively, you can use a boxed trait object for more complex cases:

```rust
fn get_closure() -> Box<dyn Fn(i32) -> i32> {
    Box::new(|x| x * 2)
}
```

## Common Use Cases
- Functional programming (map, filter, etc.)
- Event handling
- Callback functions
- Custom iterators

