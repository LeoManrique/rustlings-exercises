# Type Inference

Rust infers the type of a variable from the value it is bound to: setting it to an integer literal, for example, infers the type as `i32`, which is the default type for integers.

You can override the inferred type by adding a type annotation:

```rust
let x: u8 = 42;
```
