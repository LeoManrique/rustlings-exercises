# Arguments at the Call Site

A function's signature fixes how many values the caller must provide and what their types are. Calling a function is an expression, and the parentheses at the call site are where you pass the concrete _arguments_ that fill in for the parameters.

If the signature declares a parameter, the call must supply a value for it — and the value's type must match the parameter's type. Omitting an expected argument, or supplying one of the wrong type, is a compile-time error.

```rust
fn print_labeled_measurement(value: i32, unit_label: char) {
    println!("The measurement is: {value}{unit_label}");
}

fn main() {
    print_labeled_measurement(5, 'h');
}
```

---

**References**

[1] The Rust Programming Language — [How Functions Work](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html)
