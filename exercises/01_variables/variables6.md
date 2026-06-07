# Constants

Like immutable variables, _constants_ are values that are bound to a name and are not allowed to change, but there are a few differences between constants and variables.

First, you aren't allowed to use `mut` with constants. Constants aren't just immutable by default — they're always immutable. You declare constants using the `const` keyword instead of the `let` keyword, and **the type of the value must be annotated**:

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

Rust's naming convention for constants is to use all uppercase with underscores between words.

Constants can be declared in any scope, including the global scope, which makes them useful for values that many parts of code need to know about. They may be set only to a constant expression, not the result of a value that could only be computed at runtime. Constants are valid for the entire time a program runs, within the scope in which they were declared.

---

**References**

[1] The Rust Programming Language — [Variables and Mutability](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)
