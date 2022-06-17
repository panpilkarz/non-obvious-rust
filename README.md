Random things I found non-obvious while learning Rust

# Fundamental types

* fixed-width numeric types built-in Rust are almost all implemented directly in modern procesors
* you can make your numbers readable this way `1_000_000_000`
* unlike C and C++, Rust treats characters as distinct from the numerical types

# Strings

* there are `.green()`, `.green().bold()` etc. string methods that will make terminal output colorified
