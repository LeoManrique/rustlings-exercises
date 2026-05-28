# Custom Error Types

Nothing forces the `E` in `Result<T, E>` to be a standard-library type. Enums hold the kinds of values they hold, and they can also be parameterized — you can define your own enum whose variants describe each way an operation can fail, and return that as the error half of a `Result`.

Enums can hold generic data types in their variants:

```rust
enum Option<T> {
    Some(T),
    None,
}
```

and can take more than one type parameter, as `Result<T, E>` does. But the error type itself need not be generic at all; a plain enum whose variants enumerate the failure modes is often clearer:

```rust
enum CreationError {
    Negative,
    Zero,
}
```

A method that constructs a value can then return `Result<Self, CreationError>`, with one `Err` variant per distinct failure mode — letting callers `match` on exactly what went wrong instead of inspecting a string or guessing from `None`.
