# Updating a Value Based on the Old Value

Another common use case for hash maps is to look up a key's value and then update it based on the old value. The `or_insert` method returns a mutable reference (`&mut V`) to the value for the specified key. The mutable reference goes out of scope at the end of the loop, so all of these changes are safe and allowed by the borrowing rules.
