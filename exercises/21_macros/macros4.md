# Multiple Arms

At their core, declarative macros allow you to write something similar
to a Rust `match` expression. Macros compare a value to patterns that
are associated with particular code: the value is the literal Rust
source code passed to the macro; the patterns are compared with the
structure of that source code; and the code associated with each
pattern, when matched, replaces the code passed to the macro.

A macro body may contain more than one arm — different patterns
matching different shapes of input. Arms in a `macro_rules!` body are
written one after the other, and each arm (pattern `=>` body) must be
terminated by `;` so the parser can tell where one ends and the next
begins.

```rust
macro_rules! my_macro {
    () => {
        println!("Check out my macro!");
    };
    ($val:expr) => {
        println!("Look at this value: {}", $val);
    };
}

fn main() {
    my_macro!();
    my_macro!(7777);
}
```

---

**References**

[1] The Rust Programming Language — [Macros](https://doc.rust-lang.org/book/ch20-05-macros.html)
