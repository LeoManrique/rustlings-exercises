# Definition Order

An important difference between macros and functions is that you must
define macros or bring them into scope *before* you call them in a file,
as opposed to functions, which you can define anywhere and call anywhere.

```rust
macro_rules! my_macro {
    () => {
        println!("Check out my macro!");
    };
}

fn main() {
    my_macro!();
}
```

---

**References**

[1] The Rust Programming Language — [Macros](https://doc.rust-lang.org/book/ch20-05-macros.html)
