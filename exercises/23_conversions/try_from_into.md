# The `TryFrom` Trait

`TryFrom` is a simple and safe type conversion that may fail in a controlled way under some circumstances. Basically, this is the same as `From`. The main difference is that this should return a `Result` type instead of the target type itself. It is the reciprocal of `TryInto`.

```rust
pub trait TryFrom<T>: Sized {
    type Error;
    fn try_from(value: T) -> Result<Self, Self::Error>;
}
```

`TryFrom` is useful when performing type conversions that may not always succeed. For example, there is no way to convert an `i64` into an `i32` using the `From` trait, because an `i64` may contain a value that an `i32` cannot represent and the conversion would lose data. The `From` trait is intended for perfect conversions, while `TryFrom` informs the programmer when a type conversion could fail and lets them decide how to handle it.

Just as `From<U> for T` implies `Into<T> for U`, `TryFrom<T> for U` implies `TryInto<U> for T`.

### Usage

```rust
let big_number = 1_000_000_000_000i64;

// Using `as` cast silently truncates.
let smaller_number = big_number as i32;
assert_eq!(smaller_number, -727379968);

// Using TryFrom returns an error for out-of-range values.
let try_smaller_number = i32::try_from(big_number);
assert!(try_smaller_number.is_err());

// Returns Ok(3) for values within range.
let try_successful_smaller_number = i32::try_from(3);
assert!(try_successful_smaller_number.is_ok());
```
