# Parameters

Functions can be defined to have _parameters_: special variables that are part of a function's signature. When a function has parameters, you can provide it with concrete values for those parameters (the concrete values are called _arguments_).

In function signatures, you _must_ declare the type of each parameter:

```rust
fn call_me(num: i32) {
    // ...
}
```

This is a deliberate decision in Rust's design: requiring type annotations in function definitions means the compiler almost never needs you to use them elsewhere in the code to figure out what type you mean. The compiler is also able to give more-helpful error messages if it knows what types the function expects.

When defining multiple parameters, separate the parameter declarations with commas.

---

**References**

[1] The Rust Programming Language — [How Functions Work](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html)
