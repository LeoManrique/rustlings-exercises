# Lifetime Annotations in Struct Definitions

Structs can hold references, but they require lifetime annotations.
Declare a generic lifetime parameter inside angle brackets after the
struct name, then use it on each reference-typed field:

```rust
struct ImportantExcerpt<'a> {
    part: &'a str,
}
```

This annotation means an instance of the struct cannot outlive the
reference it holds in its field. Without such an annotation, the
compiler has no way to know how long the borrowed data must remain
valid relative to the struct, so the definition is rejected.

---

**References**

[1] The Rust Programming Language — [Validating References with Lifetimes](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html)
