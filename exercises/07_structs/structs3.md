# Methods

Methods are similar to functions: We declare them with the `fn` keyword and a name, they can have parameters and a return value, and they contain some code that's run when the method is called from somewhere else. Unlike functions, methods are defined within the context of a struct (or an enum or a trait object), and their first parameter is always `self`, which represents the instance of the struct the method is being called on.

To define the function within the context of a type, we start an `impl` (implementation) block for it. Everything within this `impl` block will be associated with that type. The method syntax goes after an instance: We add a dot followed by the method name, parentheses, and any arguments.

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

let rect = Rectangle { width: 30, height: 50 };
println!("The area is {} square pixels.", rect.area());
```

In the signature for a method, we use `&self` instead of an explicit typed parameter. The `&self` is actually short for `self: &Self`. Within an `impl` block, the type `Self` is an alias for the type that the `impl` block is for. Note that we still need to use the `&` in front of the `self` shorthand to indicate that this method borrows the `Self` instance.

Methods can take ownership of `self`, borrow `self` immutably, or borrow `self` mutably, just as they can any other parameter. Using `&self` is chosen when we don't want to take ownership and just want to read the data in the struct.

## Methods with More Parameters

Methods can take multiple parameters that we add to the signature after the `self` parameter, and those parameters work just like parameters in functions.

```rust
impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```

---

**References**

[1] The Rust Programming Language — [Method Syntax](https://doc.rust-lang.org/book/ch05-03-method-syntax.html)
