# Updating a Value Based on the Old Value

Another common use case for hash maps is to look up a key's value and then update it based on the old value. The `or_insert` method returns a mutable reference (`&mut V`) to the value for the specified key. The mutable reference goes out of scope at the end of the loop, so all of these changes are safe and allowed by the borrowing rules.

```rust
use std::collections::HashMap;

let text = "hello world wonderful world";
let mut map = HashMap::new();

for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    *count += 1;
}

println!("{map:?}");
```

---

**References**

[1] The Rust Programming Language — [Storing Keys with Associated Values in Hash Maps](https://doc.rust-lang.org/book/ch08-03-hash-maps.html)
