# The Orphan Rule

You can implement a trait on a type only if either the trait or the type, or both, are local to your crate. For example:

- You can implement standard library traits like `Display` on a custom type because that type is local.
- You can implement a local trait on `Vec<T>` in your crate because the trait is local.
- You cannot implement external traits on external types — for example, you can't implement `Display` on `Vec<T>` in your crate because both are defined in the standard library.

This restriction is part of a property called *coherence*, specifically the *orphan rule* (named because the parent type is not present). It ensures that other people's code can't break yours and vice versa. Without this rule, two crates could implement the same trait for the same type, and Rust wouldn't know which implementation to use.

Source: <https://doc.rust-lang.org/book/ch10-02-traits.html>
