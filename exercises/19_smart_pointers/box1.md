# Box for Recursive Types

The most straightforward smart pointer is a box, whose type is written `Box<T>`. Boxes allow you to store data on the heap rather than the stack. What remains on the stack is the pointer to the heap data.

A value of a recursive type can have another value of the same type as part of itself. Recursive types pose an issue because Rust needs to know at compile time how much space a type takes up. However, the nesting of values of recursive types could theoretically continue infinitely, so Rust can't know how much space the value needs. Because boxes have a known size, we can enable recursive types by inserting a box in the recursive type definition.

Because `Box<T>` is a pointer, Rust always knows how much space a `Box<T>` needs: a pointer's size doesn't change based on the amount of data it's pointing to. This means we can put a `Box<T>` inside the recursive variant instead of another value of the type directly. The `Box<T>` will point to the next value that will be on the heap rather than inside the variant.

By using a box, we've broken the infinite, recursive chain, so the compiler can figure out the size it needs to store the value. Boxes provide only the indirection and heap allocation; they don't have any other special capabilities. They also don't have the performance overhead that special capabilities incur, so they can be useful in cases like the cons list where the indirection is the only feature needed.
