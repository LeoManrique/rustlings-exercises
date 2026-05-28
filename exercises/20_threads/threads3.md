# Multiple Producers by Cloning the Transmitter

`mpsc` stands for *multiple producer, single consumer*. The way Rust's
standard library implements channels means a channel can have multiple
*sending* ends that produce values but only one *receiving* end that consumes
those values. Imagine multiple streams flowing together into one big river:
everything sent down any of the streams will end up in one river at the end.

Since channels support multiple producers, you can clone the transmitter and
pass different clones to multiple threads. All threads can send values to the
same receiver. This is useful when multiple threads need to communicate with a
single receiving thread that aggregates or processes their results.

The transmitter has a `send` method that takes the value we want to send and
returns a `Result<T, E>`; if the receiver has already been dropped, `send`
will return an error. The receiver can be treated as an iterator—for each
value received, you can process it, and when every transmitter has been
dropped the channel closes and iteration ends.
