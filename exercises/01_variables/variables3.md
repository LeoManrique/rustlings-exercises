# Initialization

A type annotation tells the compiler what type a binding has, but it does not give the binding a value. A declaration like:

```rust
let x: i32;
```

introduces `x` with type `i32`, but `x` is still uninitialized. Reading from an uninitialized variable is a compile-time error — the binding must have a value before it can be used.

You can assign the value later, as long as it happens before the first read.
