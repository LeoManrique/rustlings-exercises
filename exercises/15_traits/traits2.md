# The Orphan Rule

You can implement a trait on a type only if either the trait or the type, or both, are local to your crate. For example:

- You can implement standard library traits like `Display` on a custom type because that type is local.
- You can implement a local trait on `Vec<T>` in your crate because the trait is local.
- You cannot implement external traits on external types — for example, you can't implement `Display` on `Vec<T>` in your crate because both are defined in the standard library.

A local trait and a type that implements it look like this:

```rust
pub trait Summary {
    fn summarize(&self) -> String;
}

pub struct NewsArticle {
    pub headline: String,
    pub author: String,
    pub location: String,
}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}
```

Traits can also provide a **default implementation** that types may use as-is or override:

```rust
pub trait Summary {
    fn summarize(&self) -> String {
        String::from("(Read more...)")
    }
}

impl Summary for NewsArticle {}
```

This restriction is part of a property called *coherence*, specifically the *orphan rule* (named because the parent type is not present). It ensures that other people's code can't break yours and vice versa. Without this rule, two crates could implement the same trait for the same type, and Rust wouldn't know which implementation to use.

---

**References**

[1] The Rust Programming Language — [Traits: Defining Shared Behavior](https://doc.rust-lang.org/book/ch10-02-traits.html)
