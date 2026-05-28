# Defining and Instantiating Structs

To define a struct, we enter the keyword `struct` and name the entire struct. Then, inside curly brackets, we define the names and types of the pieces of data, which we call *fields*.

To use a struct after we've defined it, we create an *instance* of that struct by specifying concrete values for each of the fields. We create an instance by stating the name of the struct and then add curly brackets containing `key: value` pairs, where the keys are the names of the fields and the values are the data we want to store in those fields. We don't have to specify the fields in the same order in which we declared them in the struct.

To get a specific value from a struct, we use dot notation.

## Tuple Structs

Rust also supports structs that look similar to tuples, called *tuple structs*. Tuple structs have the added meaning the struct name provides but don't have names associated with their fields; rather, they just have the types of the fields. They are useful when you want to give the whole tuple a name and make the tuple a different type from other tuples, and when naming each field as in a regular struct would be verbose or redundant.

To define a tuple struct, start with the `struct` keyword and the struct name followed by the types in the tuple. Tuple struct instances are similar to tuples in that you can use a `.` followed by the index to access an individual value.

## Unit-Like Structs

You can also define structs that don't have any fields! These are called *unit-like structs* because they behave similarly to `()`, the unit type. Unit-like structs can be useful when you need to implement a trait on some type but don't have any data that you want to store in the type itself.

To define a unit-like struct, use the `struct` keyword, the name you want, and then a semicolon. No need for curly brackets or parentheses! Then, you can get an instance of the unit-like struct in a similar way: using the name you defined, without any curly brackets or parentheses.
