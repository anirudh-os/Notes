## The conditional statements

if-else

1. The Normal Way
    ```rust
    if (a < b) {
        println!("Nope");
    } else {
        println!("Yup");
    }
    ```

2. The New Way
    ```rust
    let can_vote = if my_age >= 18 {
        true
    } else {
        false
    };
    ```
- It works like a ternary operator

match

- It helps in matching a set of conditionals at once

    ```rust
    let age2 = rand::thread_rng().gen_range(1..=100);
    match age2 {
        1..=18 => println!("{}\nNot eligible!", age2),
        19..=i32::MAX => println!("{}\nEligible", age2),
        _ => println!("{}\nNot eligible!", age2)
    };
    ```

    ```bash
    $ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/rust_tutorial`
    20
    Eligible
    ```
- `1..100` acts as the range. It only counts till 99 and 100 will be ignored
- `1..=18` means count till 18
- `_` inside the match block denotes the default case

    ```rust
    let age = 18;
    let voting_age = 18;
    match age.cmp(&voting_age) {
        Ordering::Less => println!("Not eligible!"),
        Ordering::Greater => println!("Eligible"),
        Ordering::Equal => println!("Gained the right to vote")
    };
    ```

- `cmp` is a function of the standard library
- `self.cmp(&other)` returns the ordering matching the expression `self <operator> other` if true.

## Loops

1. Loop
    ```rust
    loop {
        if arr[i] % 2 == 0 {
            i += 1;
            continue;
        }
        if arr[i] == 7 {
            break;
        }

        println!("{}", arr[i]);
        i += 1;
    }
    ```

2. While
    ```rust
    while i < arr.len() {
        if arr[i] % 2 == 0 {
            i += 1;
            continue;
        }

        println!("{}", arr[i]);
        i += 1;
    }
    ```

3. For

    1. **Iterating over a range**
        + This is the most basic form of a `for` loop, where you can iterate over a range of numbers.

        ```rust
        for i in 0..5 {  // Iterates from 0 to 4
            println!("{}", i);
        }
        ```

        - `0..5` creates a range from 0 to 4 (exclusive of 5).
        - You can also use `0..=5` for inclusive ranges, which includes 5.

    2. **Iterating over an array or slice**
        - You can loop through the elements of an array or slice.

        ```rust
        let arr = [10, 20, 30];
        for &item in &arr {  // Using reference to array and destructuring
            println!("{}", item);
        }
        ```

        - `&arr` gives a reference to the array, and `&item` destructures the reference into the value.

    3. **Iterating over a vector**
        - Similar to arrays, but with a `Vec` (a dynamically sized collection).

        ```rust
        let vec = vec![1, 2, 3];
        for item in &vec {  // Iterating over references to elements
            println!("{}", item);
        }
        ```

        - The reference (`&vec`) prevents ownership issues, so you don't consume the vector.

    4. **Enumerating over an iterable**
        - You can enumerate an iterator to get both the index and the value.

        ```rust
        let vec = vec!["a", "b", "c"];
        for (index, value) in vec.iter().enumerate() {
            println!("Index: {}, Value: {}", index, value);
        }
        ```

        - `enumerate()` returns a tuple of the index and value.

    5. **Using `into_iter()`**
        - If you want to take ownership of the elements in a collection, you can use `into_iter()`.

        ```rust
        let vec = vec![1, 2, 3];
        for item in vec.into_iter() {  // Moves elements from vec
            println!("{}", item);
        }
        ```

        - `into_iter()` consumes the vector and gives ownership of its elements.

    6. **For loop with a `while` or `for` condition**
        - You can combine `for` with an explicit condition.

        ```rust
        let mut count = 0;
        for _ in 0..5 {
            count += 1;
            if count == 3 {
                break;  // Stop the loop when count reaches 3
            }
        }
        ```

        - This combines a `for` loop with a condition to control when to exit.

    7. **Looping with `step_by()`**
        - Rust allows stepping over elements in a range with `step_by()`.

        ```rust
        for i in (0..10).step_by(2) {
            println!("{}", i);  // Will print 0, 2, 4, 6, 8
        }
        ```
        - `step_by(2)` makes the loop increment by 2 each time.

    8. **Using the iter() method**
        ```rust
        let arr = [1, 2, 3, 4 ,5, 6, 7];
        for &val in arr.iter() {
            println!("{}", val);
        }
        ```
        
        - The `iter()` method returns an iterator object of the collection