# If Expressions

An `if` expression allows you to branch your code depending on conditions. You provide a condition and then state, "If this condition is met, run this block of code. If the condition is not met, do not run this block of code."

All `if` expressions start with the keyword `if`, followed by a condition. We place the block of code to execute if the condition is `true` immediately after the condition inside curly brackets. Blocks of code associated with the conditions in `if` expressions are sometimes called *arms*, just like the arms in `match` expressions.

Optionally, we can also include an `else` expression, which gives the program an alternative block of code to execute should the condition evaluate to `false`. If you don't provide an `else` expression and the condition is `false`, the program will just skip the `if` block and move on to the next bit of code.

It's worth noting that the condition in this code *must* be a `bool`. If the condition isn't a `bool`, we'll get an error. Unlike languages such as Ruby and JavaScript, Rust will not automatically try to convert non-Boolean types to a Boolean. You must be explicit and always provide `if` with a Boolean as its condition.

```rust
let number = 3;

if number < 5 {
    println!("condition was true");
} else {
    println!("condition was false");
}
```

Because `if` is an expression, the block evaluates to the value of its last expression, which lets the whole `if`/`else` be returned directly from a function.

---

**References**

[1] The Rust Programming Language — [Control Flow: if Expressions](https://doc.rust-lang.org/book/ch03-05-control-flow.html#if-expressions)
