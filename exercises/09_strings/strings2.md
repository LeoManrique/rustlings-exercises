# Borrowing a `String` as `&str`

When a function takes a string slice and you have a `String`, you can pass a
reference to the `String`. The compiler performs deref coercion, converting
`&String` to `&str` automatically.

```rust
fn first_word(s: &str) -> &str {
    let bytes = s.as_bytes();
    for (i, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &s[0..i];
        }
    }
    &s[..]
}

let my_string = String::from("hello world");
// &String is coerced to &str automatically
let word = first_word(&my_string);
// A string literal is already &str
let word2 = first_word("hello world");
```

This is the same mechanism that makes the `+` operator on strings work: its
`add` method has the signature `fn add(self, s: &str) -> String`, yet you can
pass `&String` for the second parameter because of deref coercion.

---

**References**

[1] The Rust Programming Language — [Storing UTF-8 Encoded Text with Strings](https://doc.rust-lang.org/book/ch08-02-strings.html)
