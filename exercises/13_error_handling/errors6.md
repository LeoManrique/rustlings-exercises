# Error Conversion

Using catch-all error types like `Box<dyn Error>` isn't recommended for library code where callers might want to make decisions based on the error content instead of printing it out or propagating it further. A custom error type makes it possible for callers to decide what to do next when a function returns an error — but only if every underlying failure can be turned into a variant of that type.

The bridge is conversion. Error values that have the `?` operator called on them go through the `from` function, defined in the `From` trait in the standard library, which is used to convert values from one type into another. When the `?` operator calls the `from` function, the error type received is converted into the error type defined in the return type of the current function. This is useful when a function returns one error type to represent all the ways a function might fail.

When `?` is not in play, the same conversion can be performed explicitly with `Result::map_err`, passing a constructor (or any `FnOnce(E) -> F`) that wraps the inner error into the outer one — for example, a variant of an enum whose payload *is* the foreign error:

```rust
enum ParsePosNonzeroError {
    Creation(CreationError),
    ParseInt(ParseIntError),
}
```

Each variant carries the original error inside it, so no information is lost on the way up.

---

**References**

[1] The Rust Programming Language — [Recoverable Errors with Result](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html)
