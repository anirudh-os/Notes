## The conditional statements

### if-else

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

### match

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
    hile i < arr.len() {
        if arr[i] % 2 == 0 {
            i += 1;
            continue;
        }

        println!("{}", arr[i]);
        i += 1;
    }
    ```

3. For
    ```rust
    let arr = [1, 2, 3, 4 ,5, 6, 7];
    for val in arr.iter() {
        println!("{}", val);
    }
    ```
- The `iter()` method returns an iterator object of the collection