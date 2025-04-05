**HashMaps in Rust - Notes from 'The Rust Programming Language'**

---

### 1. Introduction
- Hash maps store data as key-value pairs.
- Provided by `std::collections::HashMap`.

```rust
use std::collections::HashMap;
```

---

### 2. Creating a HashMap

#### a. Using `HashMap::new()`
```rust
let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);
```

#### b. Using `collect()` with tuples from a vector
```rust
let teams = vec![String::from("Blue"), String::from("Yellow")];
let initial_scores = vec![10, 50];

let scores: HashMap<_, _> = teams.into_iter().zip(initial_scores.into_iter()).collect();
```

#### c. Using `HashMap::with_capacity()` (preallocating space)
```rust
let mut map = HashMap::with_capacity(10);
```

---

### 3. Accessing Values
```rust
let team_name = String::from("Blue");
let score = scores.get(&team_name); // returns Option<&V>
```

- Use `match` or `if let` to handle `Option`.
- `.get()` is non-destructive and returns an immutable reference.

Example with `match`:
```rust
match scores.get("Blue") {
    Some(score) => println!("Score: {}", score),
    None => println!("No score found"),
}
```

---

### 4. Iterating Over a HashMap
```rust
for (key, value) in &scores {
    println!("{}: {}", key, value);
}
```

---

### 5. Ownership
- HashMap takes ownership of keys and values.
- Values that implement `Copy` trait (like i32) are copied.

```rust
let field_name = String::from("Favorite color");
let field_value = String::from("Blue");

let mut map = HashMap::new();
map.insert(field_name, field_value);
// field_name and field_value are moved
```

---

### 6. Updating a HashMap
- Overwriting:
```rust
scores.insert(String::from("Blue"), 25); // replaces previous value
```

- Only insert if key doesn't exist:
```rust
scores.entry(String::from("Blue")).or_insert(50);
```

- Updating based on old value:
```rust
let text = "hello world wonderful world";
let mut map = HashMap::new();

for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    *count += 1;
}
```

---

### 7. Searching and Removing

#### Searching for a key
```rust
if scores.contains_key("Blue") {
    println!("Blue is in the map.");
}
```

#### Removing a key-value pair
```rust
scores.remove("Blue"); // removes the key and its value
```

#### Removing with a match
```rust
match scores.remove("Yellow") {
    Some(value) => println!("Removed value: {}", value),
    None => println!("Key not found"),
}
```

---

### 8. Hashing
- By default, uses SipHash (resistant to DoS).
- You can specify a custom hasher by implementing the `BuildHasher` trait (rarely needed).

---

### 9. Notes
- Requires `Eq` and `Hash` traits for keys.
- Not ordered.
- Use `BTreeMap` if you need sorted keys.

---


