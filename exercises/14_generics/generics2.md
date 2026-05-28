# Generic Structs

We can also define structs to use a generic type parameter in one or more fields using the `<>` syntax. The syntax for using generics in struct definitions is similar to that used in function definitions. First, we declare the name of the type parameter inside angle brackets just after the name of the struct. Then, we use the generic type in the struct definition where we would otherwise specify concrete data types.

We can implement methods on structs and use generic types in their definitions too. Note that we have to declare `T` just after `impl` so that we can use `T` to specify that we're implementing methods on the type. By declaring `T` as a generic type after `impl`, Rust can identify that the type in the angle brackets is a generic type rather than a concrete type.
