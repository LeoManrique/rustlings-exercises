# The Result Enum

`Result` is a richer version of the `Option` type that describes possible *error* instead of possible *absence*.

The `Result` enum is defined as having two variants, `Ok` and `Err`:

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

The `T` and `E` are generic type parameters. `T` represents the type of the value that will be returned in a success case within the `Ok` variant, and `E` represents the type of the error that will be returned in a failure case within the `Err` variant. Because `Result` has these generic type parameters, we can use the `Result` type and the functions defined on it in many different situations where the success value and error value we want to return may differ.

By convention, the expected outcome is `Ok` while the unexpected outcome is `Err`. Unlike returning `None`, returning an `Err` lets a function explain *what* went wrong.

---

**References**

[1] Rust by Example — [Result](https://doc.rust-lang.org/rust-by-example/error/result.html)

[2] The Rust Programming Language — [Recoverable Errors with Result](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html)
