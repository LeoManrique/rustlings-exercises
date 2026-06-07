# The `From` Trait

The `From<T>` trait is used for value-to-value conversions while consuming the input value. It's the reciprocal of the `Into` trait.

```rust
pub trait From<T>: Sized {
    fn from(value: T) -> Self;
}
```

**Key principle:** Always prefer implementing `From` over `Into` because implementing `From` automatically provides an implementation of `Into` through a blanket implementation in the standard library. That is, `From<U> for T` implies `Into<T> for U`.

The `From` trait should be used only when the conversion is:

1. **Infallible** — the conversion cannot fail. Use `TryFrom` for fallible conversions instead of providing a `From` implementation that panics.
2. **Lossless** — information should not be lost or discarded.
3. **Value-preserving** — the conceptual kind and meaning of the resulting value should be the same.
4. **Obvious** — it should be the only reasonable conversion between two types.

## Usage

```rust
let string = "hello".to_string();
let other_string = String::from("hello");

assert_eq!(string, other_string);
```

Because `From` is implemented, the reciprocal `Into` is available as well:

```rust
let s: String = "hello".into();
```

---

**References**

[1] The Rust Standard Library — [std::convert::From](https://doc.rust-lang.org/std/convert/trait.From.html)
