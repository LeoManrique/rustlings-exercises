# Shared Mutable State with `Mutex<T>`

*Mutex* is an abbreviation for *mutual exclusion*, as in a mutex allows only
one thread to access some data at any given time. To access the data in a
mutex, a thread must first signal that it wants access by asking to acquire
the mutex's lock. The *lock* is a data structure that is part of the mutex
that keeps track of who currently has exclusive access to the data. The mutex
is described as *guarding* the data it holds via the locking system.

You must remember two rules:

1. You must attempt to acquire the lock before using the data.
2. When you're done with the data that the mutex guards, you must unlock the
   data so that other threads can acquire the lock.

We create a `Mutex<T>` using the associated function `new`. To access the data
inside, we call `lock` to acquire the lock. This call will block the current
thread so that it can't do any work until it's our turn to have the lock. The
call to `lock` would fail if another thread holding the lock panicked, so we
typically `unwrap` and have this thread panic if we're in that situation.

After we've acquired the lock, we can treat the return value as a mutable
reference to the data inside. The type system ensures that we acquire a lock
before using the value. The call to `lock` returns a `MutexGuard`, which
implements `Deref` to point at our inner data and has a `Drop` implementation
that releases the lock automatically when the guard goes out of scope.

```rust
use std::sync::{Arc, Mutex};
use std::thread;

let counter = Arc::new(Mutex::new(0));
let mut handles = vec![];

for _ in 0..10 {
    let counter = Arc::clone(&counter);
    let handle = thread::spawn(move || {
        let mut num = counter.lock().unwrap();
        *num += 1;
    });
    handles.push(handle);
}

for handle in handles {
    handle.join().unwrap();
}

println!("Result: {}", *counter.lock().unwrap());
```

`Mutex<T>` provides interior mutability: the binding can be immutable but you
can still get a mutable reference to the value inside it. In the same way
`RefCell<T>` lets you mutate contents inside an `Rc<T>`, you use `Mutex<T>` to
mutate contents inside an `Arc<T>`.

---

**References**

[1] The Rust Programming Language — [Shared-State Concurrency](https://doc.rust-lang.org/book/ch16-03-shared-state.html)
