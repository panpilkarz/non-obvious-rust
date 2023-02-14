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
* use `Rc` to act kind of like Python does
* unlike in C++, Rust reference can change where it points to
* comparing refs is comparing values; to compare addresses use `std::ptr::eq`
* references can't be null; use `Option<&T>` if want to express "nullable"

# Rules of thumb

* any type that needs to do something special when a value is dropped cannot by Copy-type
* closures are lightweight function-like values
* Rust checks if code in the doc works
* `#[inline]` is a suggestion
* there is convention to name struct constructors "new"
* pattern matching requires to match all possible values. add "_" and panic() for impossible cases
* match guard is an extra condition for match

# Error handling

* Rust doesn't have exceptions
* by default panic!() causes unwinding
* panic is per thread
* functions that can fail have a return type that say so `Result<Any, Error>`
* catch errors using match
* operator ? propagates error to the caller stack frame
* to handle errors in main use `.except()`

# Expressions

* most of the control flow tools in C are statements. In Rust they are all expressions.
* if an match can produce values
* for loop follows move-semantic and consumes the values it iterates. to avoid this, iterate over references.
* loop can return; break has argument
* loop can be labelled with lifetime and break can exists the outer loop
* divergent functions (->!) never exits

# Crates

* Rust compiles crates into .rlib files
* you should specify edition yhou code is using. 2015 is default
* `use std::fs::{self, File}` imports `both std::fs` and `std::fs::File`

