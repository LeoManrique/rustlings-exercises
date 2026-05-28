# Making Items Public with `pub`

Modules let you organize code within a crate and control the *privacy* of items. Code within a module is private by default, meaning internal implementation details are not available for outside use. You can choose to make modules and items public to expose them for external use.

By default, all items in Rust (functions, methods, structs, enums, modules, and constants) are private to parent modules. Items in a parent module cannot use private items inside child modules, but items in child modules can use items in their ancestor modules. Child modules wrap and hide their implementation details while being able to see the context in which they're defined.

Use the `pub` keyword to expose items from child modules to parent modules. Placing `pub` before an item's declaration makes that item callable from outside the module.
