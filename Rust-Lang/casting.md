# Casting

- It can be done using the `as` keyword
    ```rust
    let a: u8 = 16;
    let b: u16 = 16;
    let c = (a as u32) + (b as u32);
    ```