# Traits as Parameters

Use the `impl Trait` syntax to accept many different types that implement a trait:

```rust
pub fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}
```

Instead of a concrete type, specify the `impl` keyword and the trait name. This parameter accepts any type implementing the specified trait. In the function body, you can call any methods from the trait. Code passing any other type won't compile.

With `impl Trait`, you can have two parameters implement the same trait with potentially different concrete types:

```rust
pub fn notify(item1: &impl Summary, item2: &impl Summary) {
```

---

**References**

[1] The Rust Programming Language — [Traits: Defining Shared Behavior](https://doc.rust-lang.org/book/ch10-02-traits.html)
