# The `?` Operator and Compatible Return Types

The pattern of propagating errors is so common in Rust that Rust provides the question mark operator `?` to make this easier. The `?` placed after a `Result` value is defined to work in almost the same way as a `match` that returns early on `Err`:

If the value of the `Result` is an `Ok`, the value inside the `Ok` will get returned from this expression, and the program will continue. If the value is an `Err`, the `Err` will be returned from the whole function as if we had used the `return` keyword so that the error value gets propagated to the calling code.

```rust
fn read_username_from_file() -> Result<String, io::Error> {
    let mut username_file = File::open("hello.txt")?;
    let mut username = String::new();
    username_file.read_to_string(&mut username)?;
    Ok(username)
}
```

## Where to Use `?`

The `?` operator can only be used in functions whose return type is compatible with the value the `?` is used on. If you try to use `?` in a function (such as `main`) that returns `()`, you'll get a compile error.

To fix this, you can change the return type to `Result<(), E>`:

```rust
fn main() -> Result<(), Box<dyn Error>> {
    let greeting_file = File::open("hello.txt")?;
    Ok(())
}
```

When a `main` function returns a `Result<(), E>`, the executable will exit with a value of `0` if `main` returns `Ok(())` and will exit with a nonzero value if `main` returns an `Err` value.

---

**References**

[1] The Rust Programming Language — [Recoverable Errors with Result](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html)
