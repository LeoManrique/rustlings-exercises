# Lifetime Annotations in Function Signatures

When writing functions that return references, you often need to specify
lifetime parameters. The compiler cannot determine whether a returned
reference is borrowed from one input or another, so it needs explicit
lifetime annotations to understand the relationship between the input and
output lifetimes.

Lifetime annotations describe the relationships of lifetimes between
multiple references without affecting how long any references actually
live. Lifetime parameter names start with an apostrophe (`'`) and are
usually all lowercase and short, like `'a`. They appear after the `&` of
a reference, using a space to separate the annotation from the
reference's type:

```rust
&i32           // a reference
&'a i32        // a reference with an explicit lifetime
&'a mut i32    // a mutable reference with an explicit lifetime
```

To use lifetime annotations in function signatures, declare generic
lifetime parameters inside angle brackets between the function name and
the parameter list. A signature like
`fn foo<'a>(x: &'a str, y: &'a str) -> &'a str` tells Rust that for some
lifetime `'a`, the function takes two string slices that live at least
as long as `'a` and returns a string slice that will live at least as
long as `'a`. The lifetime of the returned reference equals the smaller
of the lifetimes of the input arguments.

---

**References**

[1] The Rust Programming Language — [Validating References with Lifetimes](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html)
