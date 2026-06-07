# Borrowing inside a `match`

Matching directly on an `Option` moves the value out of it, so the original binding can no longer be used afterwards. To inspect the contained value without consuming the `Option`, take a reference to it in the pattern:

```rust
let msg = Some("howdy");

// Take a reference to the contained string
if let Some(m) = &msg {
    println!("{}", *m);
}
```

The key distinction: using `&` in pattern matching allows you to borrow the contained value without consuming the `Option`, while matching directly on the value moves it out. The same technique applies to `match` arms when the binding needs to remain usable after the match.

---

**References**

[1] The Rust Standard Library — [std::option::Option](https://doc.rust-lang.org/std/option/enum.Option.html)
