# Rust Borrowing

## What is Borrowing?
Borrowing in Rust allows a function to access data without taking ownership. It is achieved through references (`&T` for immutable borrowing and `&mut T` for mutable borrowing).

### Syntax
```rust
let x = 5;
let y = &x; // Immutable borrow
let mut z = 10;
let w = &mut z; // Mutable borrow
```

## Rules of Borrowing
1. You can have either one mutable reference or any number of immutable references at a time.
2. References must always be valid.

## Immutable Borrowing
- Allows read-only access to the data.
- Multiple immutable borrows are allowed simultaneously.

### Example:
```rust
let x = 42;
let a = &x;
let b = &x;
println!("a: {}, b: {}", a, b); // Both borrows are valid
```

## Mutable Borrowing
- Allows modification of the borrowed data.
- Only one mutable borrow is allowed at a time.

### Example:
```rust
let mut x = 42;
let y = &mut x;
*y += 1;
println!("x: {}", x); // x is now 43
```

## Combining Immutable and Mutable References
Combining different types of references can be tricky due to Rust's strict borrowing rules. Here are the valid and invalid combinations:

### Valid Combinations:
- Any number of immutable references.
- One mutable reference (without any immutable references).

### Invalid Combinations:
- One mutable reference and one or more immutable references.
- Multiple mutable references.

### Example of Invalid Combination:
```rust
let mut x = 10;
let a = &x;
let b = &mut x; // Error: cannot borrow `x` as mutable because it is also borrowed as immutable
```

### Why these rules exist:
- To prevent data races, which occur when:
  - Two or more pointers access the same data at the same time.
  - At least one of the accesses is a write.
  - There is no synchronization mechanism.

## Dangling References
- Occur when a reference points to invalid data.
- Rust prevents this through its ownership and borrowing rules.

### Example:
```rust
fn dangle() -> &String { // Error
    let s = String::from("hello");
    &s // `s` goes out of scope, reference becomes invalid
}
```

## Lifetimes
- Specify how long a reference is valid.
- Helps the compiler ensure references are always valid.

### Syntax:
```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

## Best Practices
- Use immutable references when possible to avoid data races.
- Use mutable references carefully to maintain safety.
- Always ensure references are valid for as long as they are used.

