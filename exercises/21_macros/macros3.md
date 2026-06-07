# Exporting Macros from Modules

A `macro_rules!` macro defined inside a module is, by default, only
usable within that module. To make it available to code outside the
module where it is defined, an annotation is needed that indicates the
macro should be made available whenever the surrounding scope is brought
into view. Without this annotation, the macro can't be brought into
scope.

The relevant attribute is `#[macro_export]`, placed directly above the
`macro_rules!` definition.

```rust
mod my_module {
    #[macro_export]
    macro_rules! my_macro {
        () => {
            println!("Check out my macro!");
        };
    }
}

fn main() {
    my_macro!();
}
```

---

**References**

[1] The Rust Programming Language — [Macros](https://doc.rust-lang.org/book/ch20-05-macros.html)
