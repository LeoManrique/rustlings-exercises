# Collecting Into `Result`

`collect` can do more than gather plain values into a container — it can also turn an iterator of fallible items into a single fallible container.

Given an iterator that yields `Result<T, E>`, calling `collect` with the target type `Result<Vec<T>, E>` short-circuits: it produces `Ok(Vec<T>)` if every item is `Ok`, or the first `Err` it encounters. Asking instead for `Vec<Result<T, E>>` keeps every individual outcome — successes and failures side by side.

Choosing the return type therefore selects the behavior:

```rust
// Stops at the first error, yielding a single Result.
let xs: Result<Vec<_>, _> = iter_of_results.collect();

// Keeps every outcome, yielding a Vec of Results.
let ys: Vec<Result<_, _>> = iter_of_results.collect();
```

The turbofish (`collect::<Result<Vec<_>, _>>()`) is an alternative way to tell `collect` which collection to build when the binding's type isn't explicit.

---

**References**

[1] The Rust Standard Library — [Iterator::collect](https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.collect)
