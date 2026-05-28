# Atomic Reference Counting Across Threads

`Rc<T>` is not safe to share across threads. When `Rc<T>` manages the reference count, it adds to the count for each call to `clone` and subtracts when each clone is dropped. But it doesn't use any concurrency primitives to ensure that changes to the count cannot be interrupted by another thread. This could lead to wrong counts—subtle bugs that could result in memory leaks or a value being dropped before you're done with it.

`Arc<T>` is a type like `Rc<T>` that is safe to use in concurrent situations. The **a** stands for **atomic**, meaning it's an _atomically reference-counted_ type. Atomics are an additional concurrency primitive that work like primitive types but are safe to share across threads.

Not all primitive types are atomic because thread safety comes with a performance penalty that you only want to pay when necessary. If you're performing operations on values within a single thread, your code can run faster if it doesn't have to enforce the guarantees atomics provide.

`Arc<T>` and `Rc<T>` have the same API, so you fix a multi-threaded program by changing the `use` line, the call to `new`, and the call to `clone`.
