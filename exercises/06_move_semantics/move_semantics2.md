# Clone

If you want to deeply copy the heap data of a value such as `String` or `Vec`, not just the stack data (pointer, length, capacity), use the `clone` method:

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {s1}, s2 = {s2}");
}
```

After cloning, both bindings own independent allocations and both remain valid. This is the way to keep an original value usable while still handing a value of the same type off to code that will consume it.

When you see a call to `clone`, you know that some arbitrary code is being executed and that code may be expensive.
