# Nested Paths from `std`

The standard `std` library is built-in and doesn't require changes to `Cargo.toml`, but you do need to use `use` to bring its items into scope.

When you need several items that share a common path prefix, nested paths clean up multiple `use` statements into a single line. List the shared prefix once, then list the items inside braces separated by commas:

```rust
use std::{cmp::Ordering, io};
```

This brings both `std::cmp::Ordering` and `std::io` into scope in one line. The same form works for two items that live in the same submodule, letting one `use` statement pull a whole set of names directly into the current scope.

---

**References**

[1] The Rust Programming Language — [Bringing Paths into Scope with the use Keyword](https://doc.rust-lang.org/book/ch07-04-bringing-paths-into-scope-with-the-use-keyword.html)
