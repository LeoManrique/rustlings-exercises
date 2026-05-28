# Creating a `String` from a `&str`

Rust has two string types: the string slice `str` (usually seen as `&str`) and
the `String` type from the standard library. String literals are stored as
string slices in the program's binary. The `String` type is a growable,
mutable, owned, UTF-8 encoded string type implemented as a wrapper around a
vector of bytes.

Initialize a `String` with data using the `to_string` method (available on
types implementing `Display`) or `String::from`:

```rust
let s = "initial contents".to_string();
let s = String::from("initial contents");
```

Both methods are equivalent; choice is a matter of style.
