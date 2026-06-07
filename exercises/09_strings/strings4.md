# Identifying `&str` vs `String`

String literals are stored as string slices (`&str`) in the program's binary.
A `String` is produced by methods and macros that allocate an owned,
UTF-8 encoded buffer:

- `String::from(...)` — explicit construction
- `.to_string()` — available on types implementing `Display`
- `.to_owned()` — converts a borrowed `&str` into an owned `String`
- `.into()` — converts when the target type (`String`) can be inferred
- `format!(...)` — works like `println!` but returns a `String`

```rust
let mut s = String::from("foo");
s.push_str("bar"); // append a string slice
s.push('!');       // append a single char
// s is now "foobar!"

let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // s1 is moved; s2 is borrowed via deref coercion

let s1 = String::from("tic");
let s2 = String::from("tac");
let s3 = String::from("toe");
let s = format!("{s1}-{s2}-{s3}"); // no ownership taken
```

Methods that return owned data produce a `String` (for example, `replace` and
`to_lowercase`), while methods that return a view into existing data — such as
`trim` or slicing with `&s[a..b]` — produce a `&str`.

Slicing uses byte indices, not character indices. Character indexing can be
done using `s.chars().nth(INDEX)`.

---

**References**

[1] The Rust Programming Language — [Storing UTF-8 Encoded Text with Strings](https://doc.rust-lang.org/book/ch08-02-strings.html)
