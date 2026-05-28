# Mutable Parameter Bindings

Function parameters are bindings, and like any binding they are immutable by default. You can mark a parameter as mutable directly in the signature by writing `mut` before its name:

```rust
fn append(mut data: String) -> String {
    data.push_str("!");
    data
}
```

This is the same `mut` keyword used on `let` bindings. It does not change the function's type — callers and the parameter type are unaffected — it only permits the owned value, once moved in, to be mutated through this binding.
