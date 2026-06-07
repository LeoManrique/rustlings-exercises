# Adding a Key and Value Only If a Key Isn't Present

Although the number of key and value pairs is growable, each unique key can only have one value associated with it at a time. If you insert a key and a value into a hash map and then insert that same key with a different value, the value associated with that key will be replaced.

It's common to check whether a particular key already exists in the hash map with a value. Hash maps have a special API for this called `entry` that takes the key you want to check as a parameter. The return value of the `entry` method is an enum called `Entry` that represents a value that might or might not exist.

The `or_insert` method on `Entry` is defined to return a mutable reference to the value for the corresponding `Entry` key if that key exists, and if not, it inserts the parameter as the new value for this key and returns a mutable reference to the new value. This technique is much cleaner than writing the logic ourselves and plays more nicely with the borrow checker.

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);

// Only inserts "Yellow" because it has no entry yet.
scores.entry(String::from("Yellow")).or_insert(50);
// Does not overwrite "Blue" because it already exists.
scores.entry(String::from("Blue")).or_insert(50);

let team = String::from("Blue");
let score = scores.get(&team).copied().unwrap_or(0);
println!("{team}: {score}");

for (key, value) in &scores {
    println!("{key}: {value}");
}
```

---

**References**

[1] The Rust Programming Language — [Storing Keys with Associated Values in Hash Maps](https://doc.rust-lang.org/book/ch08-03-hash-maps.html)
