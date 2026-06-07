# Type Inference

Rust infers the type of a variable from the value it is bound to: setting it to an integer literal, for example, infers the type as `i32`, which is the default type for integers.

You can override the inferred type by adding a type annotation:

```rust
let x: u8 = 42;
```

---

**References**

[1] The Rust Programming Language — [Variables and Mutability](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)
