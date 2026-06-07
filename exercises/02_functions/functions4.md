# Return Types

Functions can return values to the code that calls them. We don't name return values, but we must declare their type after an arrow (`->`):

```rust
fn is_even(num: i64) -> bool {
    num % 2 == 0
}
```

The return type is part of the signature, just like parameter types. If a function's body produces a value but the signature is missing its `->` arrow and type, the compiler can't know what the caller should expect back, and the function will fail to compile.

---

**References**

[1] The Rust Programming Language — [How Functions Work](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html)
