# Cargo

Cargo is the native package manager for rust. It is used to create, build and manage projects and their dependencies.

## Creating packages with Cargo

```bash
$ cargo new project_name
```

* Cargo inherently initializes a git repo if already not done so. Git files won’t be generated if you run ``` cargo new ``` within an existing Git repository
    * You can override this behavior by using ``` cargo new --vcs=git ```.
* Cargo, here, creates:
    1. '**src**' directory having **main.rs** file
    2. '**Cargo.toml**' file[^1]
    3. A '**.gitignore**' file

### The toml file

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

* The first line ```[package]```indicates that the following statements configure a package.
    * The packages of code are called **crates**.
* The last line ```[dependencies]``` is the start of the section where you list out the dependencies for your project.

## Building a Project with Cargo

The command used is:
```bash
cargo build
```
* The executable will be saved in the newly created directory **target**
    * the path for the executable is './target/debug/project_name.exe'
* Running cargo build for the first time also causes Cargo to create a new file at the top level: Cargo.lock. This file keeps track of the exact versions of dependencies in your project.
* ```cargo run``` command can be used to compile and run the code
* ```cargo check``` command makes cargo compile the code but does not let it produce an executable

For the documentation of cargo, refer [this](https://doc.rust-lang.org/cargo/)








[^1]:More on toml [here](https://toml.io/en/)