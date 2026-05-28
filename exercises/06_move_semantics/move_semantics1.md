# Ownership Transfer on Function Call

Passing a value to a function works similarly to assigning it to a variable: it will move or copy. With heap-owning types like `Vec` or `String`, the value moves into the function's parameter and is no longer valid in the caller.

```rust
fn main() {
    let s = String::from("hello");  // s comes into scope

    takes_ownership(s);             // s's value moves into the function
                                    // and is no longer valid here
}

fn takes_ownership(some_string: String) {
    println!("{some_string}");
}
```

If you try to use a variable after it's been moved into a function, Rust throws a compile-time error. Returning the value from the function moves ownership back out to the caller.
