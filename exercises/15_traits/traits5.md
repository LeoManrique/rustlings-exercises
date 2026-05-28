# Multiple Trait Bounds with `+`

Specify more than one trait bound using the `+` syntax. If you want a parameter to provide methods from two traits at once:

```rust
pub fn notify(item: &(impl Summary + Display)) {
    println!("Breaking news! {}", item.summarize());
}
```

The `+` syntax also works with trait bounds on generic types:

```rust
pub fn notify<T: Summary + Display>(item: &T) {
    println!("Breaking news! {}", item.summarize());
}
```

With both trait bounds, the function body can call methods from either trait on the parameter.

Source: <https://doc.rust-lang.org/book/ch10-02-traits.html>
