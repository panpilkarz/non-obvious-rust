Random things I found non-obvious (as a C and Python dev) while learning Rust

# Fundamental types

* fixed-width numeric types built-in Rust are almost all implemented directly in modern procesors
* you can make your numbers readable this way `1_000_000_000`
* unlike C and C++, Rust treats characters as distinct from the numerical types
* there are 128-bit integeres: `u128`, `i128`

# Strings

* there are `.green()`, `.green().bold()` etc. string methods that will make terminal output colorified

# Memory management

* moves make source uninitialised
* tuple that holds only Copy-types, is Copy-type
* if struct holds only Copy-types, you can make it Copy-type by declaring `#[derive(Copy, Clone)]`
* `Rc` (reference count) type, unlike `Arc` (atomic reference count), is not safe to share between threads, becasue it used fast non-thread-safe code to update its reference count. Otherwise the two types are equilavent.
* use `Rc` to act kind of like Python
* unlike in C++, Rust reference can change where it points to
* comparing refs is comparing values; to compare addresses use `std::ptr::eq`
* references can't be null; use `Option<&T>` if want to express "nullable"

# Rules of thumb

* any type that needs to do something special when a value is dropped cannot by Copy-type
