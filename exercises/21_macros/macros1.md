# Macro Invocation Syntax

Rust provides a powerful macro system that allows metaprogramming. Macros
look like functions, except that their name ends with a bang `!`, but
instead of generating a function call, macros are expanded into source
code that gets compiled with the rest of the program.

```rust
macro_rules! say_hello {
    () => {
        println!("Hello!")
    };
}

fn main() {
    // This call will expand into `println!("Hello!")`
    say_hello!()
}
```

Unlike macros in C and other languages, Rust macros are expanded into
abstract syntax trees, rather than string preprocessing, so you don't get
unexpected precedence bugs.

---

**References**

[1] Rust by Example — [macro_rules!](https://doc.rust-lang.org/rust-by-example/macros.html)
