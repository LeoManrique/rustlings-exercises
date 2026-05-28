# `AsRef` and `AsMut`

`AsRef` and `AsMut` allow for cheap reference-to-reference conversions. Unlike the consuming conversions seen so far, these operate on references and are zero-cost.

```rust
pub trait AsRef<T> where T: ?Sized {
    fn as_ref(&self) -> &T;
}

pub trait AsMut<T> where T: ?Sized {
    fn as_mut(&mut self) -> &mut T;
}
```

These traits enable functions to accept arguments of different types as long as they can be converted to a specified reference type — a way to write flexible generic code that works with multiple input types.

**These traits must not fail.** If the conversion can fail, use a dedicated method returning `Option<T>` or `Result<T, E>`. They are designed for cheap conversions; for costly conversions, implement `From<&T>` or write a custom function instead.

`AsRef` auto-dereferences if the inner type is a reference or mutable reference: `foo.as_ref()` works the same whether `foo` has type `&mut Foo` or `&&mut Foo`. `AsMut` behaves analogously for mutable references.

### Trait bound for flexible parameters

```rust
fn is_hello<T: AsRef<str>>(s: T) {
    assert_eq!("hello", s.as_ref());
}

let s = "hello";
is_hello(s);

let s = "hello".to_string();
is_hello(s);
```

This function accepts both `&str` and `String` because both implement `AsRef<str>`.
