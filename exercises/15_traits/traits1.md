# Implementing a Trait on a Type

A type's behavior consists of the methods we can call on that type. Different types share the same behavior if we can call the same methods on all of them. Trait definitions group method signatures together to define a set of behaviors necessary to accomplish some purpose.

To declare a trait, use the `trait` keyword followed by the trait name. Inside the curly brackets, declare method signatures that describe the behaviors of types implementing this trait. After the method signature, use a semicolon instead of providing an implementation. Each type implementing this trait must provide its own custom behavior for the method body. The compiler enforces that any type with the trait will have the method defined with this exact signature.

Implementing a trait on a type is similar to implementing regular methods. After `impl`, put the trait name you want to implement, use the `for` keyword, then specify the type name:

```rust
impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}
```

Within the `impl` block, use curly brackets and fill in the method body with the specific behavior desired for that particular type.

Source: <https://doc.rust-lang.org/book/ch10-02-traits.html>
