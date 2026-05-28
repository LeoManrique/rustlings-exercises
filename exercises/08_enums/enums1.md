# Defining an Enum

Where structs give you a way of grouping together related fields and data, enums give you a way of saying a value is one of a possible set of values. An enum value can only be one of its variants, but all variants are still treated as the same type when the code is handling situations that apply to any kind of that value.

We express this concept in code by listing the possible kinds the value can be. These are the variants of the enum:

```rust
enum IpAddrKind {
    V4,
    V6,
}
```

We can create instances of each variant by using the `::` syntax. Note that the variants of the enum are namespaced under its identifier, and we use a double colon to separate the two. This is useful because now both values `IpAddrKind::V4` and `IpAddrKind::V6` are of the same type: `IpAddrKind`.

Source: <https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html>
