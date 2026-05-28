# Struct Update Syntax

It's often useful to create a new instance of a struct that includes most of the values from another instance of the same type, but changes some of them. You can do this using struct update syntax.

Using struct update syntax, you can achieve this with less code. The syntax `..` specifies that the remaining fields not explicitly set should have the same value as the fields in the given instance. The `..instance` must come last to specify that any remaining fields should get their values from the corresponding fields in that instance, but you can choose to specify values for as many fields as you want in any order, regardless of the order of the fields in the struct's definition.

Note that the struct update syntax uses `=` like an assignment; this is because it moves the data. If a field of a non-`Copy` type is moved into the new instance, you can no longer use that field of the original instance. However, fields whose types implement the `Copy` trait would be copied rather than moved.
