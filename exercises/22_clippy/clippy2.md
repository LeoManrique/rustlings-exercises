# For Loops Over Fallibles

Both `Option` and `Result` implement the `IntoIterator` trait, which allows
using them in a `for` loop. A `for` loop over `Option` or `Result` will iterate
either 0 (if the value is `None`/`Err(_)`) or 1 time (if the value is
`Some(_)`/`Ok(_)`). This is not very useful and is more clearly expressed via
`if let`.

A `for` loop can also be accidentally written with the intention to call a
function multiple times, while the function returns `Some(_)`; in these cases
a `while let` loop should be used instead.

The "intended" use of `IntoIterator` implementations for `Option` and `Result`
is passing them to generic code that expects something implementing
`IntoIterator`. For example using `.chain(option)` to optionally add a value
to an iterator.

Clippy flags:

```rust
let opt: Option<i32> = Some(42);
for val in opt {
    println!("{val}");
}
```

and suggests:

```rust
let opt: Option<i32> = Some(42);
if let Some(val) = opt {
    println!("{val}");
}
```

---

**References**

[1] rust-clippy — [GitHub repository](https://github.com/rust-lang/rust-clippy)
