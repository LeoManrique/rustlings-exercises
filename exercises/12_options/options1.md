# The Option Enum

`Option<T>` is an enum in Rust's standard library that represents an optional value. Every `Option` is either `Some(value)` and contains a value of type `T`, or `None` and contains no value.

```rust
enum Option<T> {
    Some(T),
    None,
}
```

By using the `Option<T>` enum, we can express the abstract concept of an optional value, and because `Option<T>` is generic, we can use this abstraction no matter what the type of the optional value is.

## Extracting the contained value

- `unwrap()` returns the contained `Some` value, consuming `self`. Panics if the value is `None`. While convenient, this is generally discouraged for error handling since panics may abort the entire program.
- `expect(msg)` is similar to `unwrap()` but allows providing a custom panic message. The message should describe why you expect the `Option` to be `Some`.
- `unwrap_or(default)` returns the contained `Some` value or a provided default.

---

**References**

[1] The Rust Standard Library — [std::option::Option](https://doc.rust-lang.org/std/option/enum.Option.html)

[2] The Rust Programming Language — [Generic Data Types: In Enum Definitions](https://doc.rust-lang.org/book/ch10-01-syntax.html#in-enum-definitions)
