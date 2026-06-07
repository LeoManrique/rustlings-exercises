# Handling Multiple Conditions with `else if`

You can use multiple conditions by combining `if` and `else` in an `else if` expression. When this program executes, it checks each `if` expression in turn and executes the first body for which the condition evaluates to `true`. Once it finds one, it doesn't even check the rest.

```rust
let number = 6;

if number % 4 == 0 {
    println!("number is divisible by 4");
} else if number % 3 == 0 {
    println!("number is divisible by 3");
} else if number % 2 == 0 {
    println!("number is divisible by 2");
} else {
    println!("number is not divisible by 4, 3, or 2");
}
```

Using too many `else if` expressions can clutter your code, so if you have more than one, you might want to refactor your code.

Because each arm produces the function's result, every arm must yield the same type. Bare string literals have type `&'static str`, so they can be returned directly without any extra reference or borrow.

---

**References**

[1] The Rust Programming Language — [Control Flow: Handling Multiple Conditions with else if](https://doc.rust-lang.org/book/ch03-05-control-flow.html#handling-multiple-conditions-with-else-if)
