# Waiting for Threads with `JoinHandle`

Spawned threads may not run at all, or may end prematurely, when the main
thread exits. Fix this by saving the return value of `thread::spawn` in a
variable. The return type is `JoinHandle<T>`. Calling the `join` method on a
`JoinHandle<T>` waits for its thread to finish.

```rust
use std::thread;

let handle = thread::spawn(|| {
    for i in 1..10 {
        println!("hi {i} from the spawned thread");
    }
});

handle.join().unwrap();
```

Calling `join` on the handle *blocks* the thread currently running until the
thread represented by the handle terminates. Blocking means that thread is
prevented from performing work or exiting.

A `move` closure lets the spawned thread take ownership of values from the
enclosing scope:

```rust
use std::thread;

let v = vec![1, 2, 3];

let handle = thread::spawn(move || {
    println!("Here's a vector: {v:?}");
});

handle.join().unwrap();
```

Once a value is sent, `recv` returns it in a `Result<T, E>`; likewise `join`
returns a `Result` containing the value the closure produced, so you can
collect each thread's return value as its handle is joined.

---

**References**

[1] The Rust Programming Language — [Using Threads to Run Code Simultaneously](https://doc.rust-lang.org/book/ch16-01-threads.html)
