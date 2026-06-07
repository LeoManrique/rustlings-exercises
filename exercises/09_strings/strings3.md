# String Methods and Concatenation

The standard library provides methods that handle string complexity correctly,
including searching and substitution.

**Appending:** Use `push_str()` to append a string slice, or `push()` to append
a single character:

```rust
let mut s = String::from("foo");
s.push_str("bar");  // s is now "foobar"
s.push('!');        // s is now "foobar!"
```

**Concatenation with `+`:**

```rust
let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2;  // s1 is moved; s2 is referenced
```

The `+` operator takes ownership of `self` (so `s1` becomes invalid) but
borrows the second parameter.

**Formatting:** For multiple concatenations, the `format!` macro is more
readable:

```rust
let s = format!("{s1}-{s2}-{s3}");
```

`format!` works like `println!` but returns a `String` and doesn't take
ownership of its parameters.

---

**References**

[1] The Rust Programming Language — [Storing UTF-8 Encoded Text with Strings](https://doc.rust-lang.org/book/ch08-02-strings.html)
