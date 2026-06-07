# Multiple Producers by Cloning the Transmitter

`mpsc` stands for *multiple producer, single consumer*. The way Rust's
standard library implements channels means a channel can have multiple
*sending* ends that produce values but only one *receiving* end that consumes
those values. Imagine multiple streams flowing together into one big river:
everything sent down any of the streams will end up in one river at the end.

```rust
use std::sync::mpsc;
use std::thread;

let (tx, rx) = mpsc::channel();

thread::spawn(move || {
    tx.send(String::from("hi")).unwrap();
});

let received = rx.recv().unwrap();
println!("Got: {received}");
```

Since channels support multiple producers, you can clone the transmitter and
pass different clones to multiple threads. All threads can send values to the
same receiver. This is useful when multiple threads need to communicate with a
single receiving thread that aggregates or processes their results.

```rust
use std::sync::mpsc;
use std::thread;

let (tx, rx) = mpsc::channel();
let tx2 = tx.clone();

thread::spawn(move || tx.send(String::from("from thread 1")).unwrap());
thread::spawn(move || tx2.send(String::from("from thread 2")).unwrap());

for received in rx {
    println!("Got: {received}");
}
```

The transmitter has a `send` method that takes the value we want to send and
returns a `Result<T, E>`; if the receiver has already been dropped, `send`
will return an error. The receiver can be treated as an iterator—for each
value received, you can process it, and when every transmitter has been
dropped the channel closes and iteration ends.

---

**References**

[1] The Rust Programming Language — [Using Message Passing to Transfer Data Between Threads](https://doc.rust-lang.org/book/ch16-02-message-passing.html)
