# Useful Stuff

##  Ownership and Borrowing

1. v.iter() borrows an immutable reference of v
2. v.remove(i) needs a mutable reference to v

```rust
/// Removes all the zeros in-place from a vector of integers.
fn remove_zeros(v: &mut Vec<i32>) {
    for (i, t) in v.iter().enumerate().rev() {
        if *t == 0 {
            v.remove(i);
            v.shrink_to_fit();
        }
    }
}
```

This would give- `v.remove(i) cannot borrow v as mutable`

3. similarly s.as_bytes() produces a mutable reference to s

