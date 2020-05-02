# Rust
Rustup toolchain multiplexer:

    rustup update
    rustup doc --book
    rustup doc --std
    rustup doc std::iter::Iterator
    rustup doc --reference

Cargo is your front end to everything:

    cargo new --bin hello
    cargo new --lib foo
    cargo clippy # also runs `cargo check`
    cargo build
    cargo run -- arg1
    cargo test
    cargo fmt --all -- --check

Get the compiler to explain an error:

    rustc --explain E0208

## Move, Copy, Clone.
These rust docs give the best explaination:

    std::marker::Copy
    std::clone::Clone

By default, variables have "move" semantics unless they derrive a Copy
implementation.

Clone is a bit more involved - sometimes a data structure references data on
the heap so it needs a "deep" copy, which is what clone is.
