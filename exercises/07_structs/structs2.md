# Struct Update Syntax

It's often useful to create a new instance of a struct that includes most of the values from another instance of the same type, but changes some of them. You can do this using struct update syntax.

Without the update syntax, we set each field explicitly, often repeating values from the old instance:

```rust
let user2 = User {
    active: user1.active,
    username: user1.username,
    email: String::from("another@example.com"),
    sign_in_count: user1.sign_in_count,
};
```

Using struct update syntax, you can achieve this with less code. The syntax `..` specifies that the remaining fields not explicitly set should have the same value as the fields in the given instance. The `..instance` must come last to specify that any remaining fields should get their values from the corresponding fields in that instance, but you can choose to specify values for as many fields as you want in any order, regardless of the order of the fields in the struct's definition.

```rust
let user2 = User {
    email: String::from("another@example.com"),
    ..user1
};
```

Note that the struct update syntax uses `=` like an assignment; this is because it moves the data. If a field of a non-`Copy` type is moved into the new instance, you can no longer use that field of the original instance. However, fields whose types implement the `Copy` trait would be copied rather than moved.

---

**References**

[1] The Rust Programming Language — [Defining and Instantiating Structs](https://doc.rust-lang.org/book/ch05-01-defining-structs.html)
