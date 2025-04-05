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

4. Slices:

| Type | Description | Heap or Stack | Notes |
| --- | --- | --- | --- |
| `Vec<i32>` | A growable, heap-allocated vector | Heap | Owns its contents |
| `&Vec<i32>` | A reference to a heap-allocated vector | Stack | Still points to heap data |
| `&[i32]` | A **slice** of a vector or array | Stack | Doesn't own data; like a view |
| `&str` | A slice of a string (`&[u8]` under the hood) | Stack | Like `&[i32]` but for text |

5. Iterators:

| Iterator | What it yields | Needs `.copied()` / `.cloned()`? |
| --- | --- | --- |
| `list.iter()` | `&i32` | Yes (`.copied()` to get `i32`) |
| `list.into_iter()` | `i32` (owned) | No |
| `list.clone().into_iter()` | owned `i32` from fresh Vec | No |

6. Modules and crates:

| Keyword | Purpose |
| --- | --- |
| `mod menu;` | Declares a **module** (i.e., tells the compiler to include `menu.rs`) |
| `use crate::menu::something;` | **Imports** items from another module so you can use them directly |
| `crate::menu::something` | Fully qualified **path** to an item defined in another module |
