# Clone-on-Write

`Cow<'a, B>` is a smart pointer that provides clone-on-write functionality. It can enclose and provide immutable access to borrowed data, and clone the data lazily when mutation or ownership is required. The type is designed to work with general borrowed data via the `ToOwned` trait.

`Cow` is an enum with two variants:

- **`Borrowed(&'a B)`** — holds a reference to borrowed data
- **`Owned(<B as ToOwned>::Owned)`** — holds owned data

The key benefit is efficiency: if you never need to mutate the data, no allocation or cloning occurs. Only when mutation is required does `Cow` clone the data into an owned form.

Key methods:

- **`to_mut()`** — acquires a mutable reference to the owned form, cloning if necessary.
- **`into_owned()`** — extracts the owned data, cloning if it was borrowed.

When constructed from a borrowed reference, the value starts in the `Borrowed` variant and only transitions to `Owned` upon mutation. When constructed from an already-owned value, it starts—and stays—in the `Owned` variant regardless of whether mutation occurs.
