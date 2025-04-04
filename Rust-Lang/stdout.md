# stdout

## write! and writeln!

### **1\. `write!(f, "{:<5} {:<30} {}", self.id, self.name, status_symbol)`**

#### **Purpose**

This line **formats and writes a single task** into a buffer or output stream using `write!()`.

#### **Breaking It Down**

-   **`write!(f, "...", self.id, self.name, status_symbol)`**

    -   `write!()` is a macro used to format and write text into a given output stream (`f`).

    -   The `f` parameter is usually an instance of `std::fmt::Formatter`, used in Rust's `Display` or `Debug` trait implementations.

-   **`"{:<5} {:<30} {}"`**

    -   This is the format string, defining how the values should be arranged:

        -   `:<5` → Left-align the first value (`ID`) in a **5-character-wide** space.

        -   `:<30` → Left-align the second value (`Task Name`) in a **30-character-wide** space.

        -   `{}` → The third value (`Status Symbol`) has no width constraint and is placed normally.

### **2\. `writeln!(writer, "\n\n{:<5} {:<30} {}", "ID", "Name", "Status").unwrap();`**

#### **Purpose**

This line writes the **table header** (`ID`, `Name`, `Status`) into the `writer`.

#### **Breaking It Down**

-   **`writeln!(writer, "\n\n...")`**

    -   `writeln!()` writes a formatted string to `writer` **and automatically appends a newline (`\n`)**.

    -   The `"\n\n"` at the start **adds two blank lines** before printing the header, improving readability.

-   **`"{:<5} {:<30} {}"`**

    -   Uses the **same formatting as before**, ensuring the header aligns with the tasks.

### **3\. `writeln!(writer, "{}", "-".repeat(50)).unwrap();`**

#### **Purpose**

This line prints a **separator line** (`--------------------------------------------------`) to visually separate the header from the task list.

#### **Breaking It Down**

-   **`"{}".format("-".repeat(50))`**

    -   `"-".repeat(50)` → Creates a string of 50 dashes (`--------------------------------------------------`).

    -   `"{}"` → Formats it as a string.

-   **Why `.unwrap()`?**

    -   `writeln!()` returns a `Result<>`, and `.unwrap()` ensures it **panics if an error occurs** (e.g., if writing to a closed file).

### **Difference Between `write!()`, `writeln!()` and `print!()`, `println!()`**

#### **1\. `write!()` and `writeln!()`**

These macros are used for **formatted output to a specific writer (not directly to the console)**.

-   **Used when writing to a file, buffer, or custom output stream.**

-   **Requires a writer (like `stdout`, a file, or a buffer).**

-   **More flexible** since it works with different output destinations.

-   `writeln!()` adds a newline (`\n`) automatically, while `write!()` does not.

#### **Example: Writing to a file**

```rust
use std::fs::File;\
use std::io::{self, Write};

fn main() -> io::Result<()> {\
    let mut file = File::create("output.txt")?;

    writeln!(file, "Hello, world!")?;  // Writes to file with a newline\
    write!(file, "This is on the same line")?; // Writes to file without a newline

    Ok(())\
}
```
👉 This writes to output.txt instead of printing to the screen.

2. print!() and println!()

These macros directly print to the standard output (stdout), which is usually the console.

    Always prints to the screen.

    No need for a writer.

    println!() automatically adds a newline, while print!() does not.

#### Example: Printing to the console

```rust
fn main() {
    print!("Hello, ");
    println!("world!");
}
```
👉 Output:
```bash
Hello, world!

```
(print!() does not add a newline, so "world!" appears on the same line.)

### **Key Differences at a Glance**

| Feature | `write!()` / `writeln!()` | `print!()` / `println!()` |
| --- | --- | --- |
| **Output Destination** | A writer (file, buffer, etc.) | Always the console (`stdout`) |
| **Requires a Writer?** | Yes (`File`, `Vec<u8>`, etc.) | No |
| **Adds Newline?** | `write!()` → No, `writeln!()` → Yes | `print!()` → No, `println!()` → Yes |
| **Use Case** | Writing to files, logging, or buffers | Printing to the terminal |

* * * * *

### **Why Use `write!()` in Your Program?**

-   **Flexibility** → Can redirect output to a file, a UI component, or another program.

-   **Better structure** → Keeps display logic separate from business logic.

-   **Performance** → Directly writing to a `BufWriter` is more efficient than multiple `println!()` calls.

* * * * *

### **When Should You Use Each?**

✅ **Use `println!()`** for simple console output.\
✅ **Use `writeln!()`** when working with files or custom outputs.
