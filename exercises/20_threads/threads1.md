# Waiting for Threads with `JoinHandle`

Spawned threads may not run at all, or may end prematurely, when the main
thread exits. Fix this by saving the return value of `thread::spawn` in a
variable. The return type is `JoinHandle<T>`. Calling the `join` method on a
`JoinHandle<T>` waits for its thread to finish.

Calling `join` on the handle *blocks* the thread currently running until the
thread represented by the handle terminates. Blocking means that thread is
prevented from performing work or exiting.

Once a value is sent, `recv` returns it in a `Result<T, E>`; likewise `join`
returns a `Result` containing the value the closure produced, so you can
collect each thread's return value as its handle is joined.
