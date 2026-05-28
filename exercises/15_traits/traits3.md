# Default Implementations

Sometimes it's useful to have default behavior for some or all trait methods instead of requiring implementations on every type. When implementing the trait on a type, you can keep or override each method's default behavior.

Specify a default implementation by providing a method body in the trait definition:

```rust
pub trait Summary {
    fn summarize(&self) -> String {
        String::from("(Read more...)")
    }
}
```

To use a default implementation, specify an empty `impl` block:

```rust
impl Summary for NewsArticle {}
```

You can still call the method on instances as normal, and the default body runs.

Default implementations can call other methods in the same trait, even if those methods don't have a default implementation. Note: you cannot call the default implementation from an overriding implementation of the same method.

Source: <https://doc.rust-lang.org/book/ch10-02-traits.html>
