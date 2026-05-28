# Function Definition

You declare a new function with the `fn` keyword, followed by a function name and a set of parentheses. The curly brackets tell the compiler where the function body begins and ends:

```rust
fn call_me() {
    // body
}
```

Rust code uses _snake case_ as the conventional style for function names: all letters lowercase, with underscores separating words.

You can call any function you've defined by entering its name followed by a set of parentheses. Rust doesn't care where you define your functions, only that they're defined somewhere in a scope that can be seen by the caller.
