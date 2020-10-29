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

## Result, Option
- Result<T, E> is either Ok(T) or Err(E)
- Option<T> is either Some(T) or None.

The preferred way to handle these is explicitly, using a match:

    match opt {
        Some(v) => v,
        None => 0,
    }

    match res {
        Ok(v) => println!("working {:?}", v),
        Err(e) => println!("error {:?}", e),
    }

Or using the shorthand unwrap functions:

    opt.unwrap_or_default()
    res.unwrap_or(default_value)
    opt.unwrap_or_else(|x| 2 * x)

Try to avoid using `unwrap()` or `expect()` which cause panics.

    "4".parse().unwrap();
    "4".parse().expect("Same as unwrap, but with error message");

## `ok_or` (Option only)
Transforms the Option<T> into a Result<T, E>, mapping Some(v) to Ok(v) and None
to Err(err).

    opt.ok_or("Error message, if Option was None")
    opt.ok_or_else(|x| 2 * x)

## Try (Result only)
You can use the "try" operator "?" to unwrap Results, or propagate the error:

    fn write_to_file_question() -> Result<(), std::io::Error> {
        let mut file = File::create("my_best_friends.txt")?;
        file.write_all(b"This is a list of my best friends.")?;
        Ok(())
    }

Remember: This expands to returning an Err(), so the return type has to be a
Result.

See more: https://doc.rust-lang.org/std/macro.try.html

## parse() -> Result
Use parse to convert strings into other types:

    let n: usize = "4".parse().unwrap();
    let n: usize = "4".parse()?;

Remember: it returns a Result! So handle that appropriately. Avoid unwrap().

## Lifetime elision
Rust has a great chapter on this:
- https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html#lifetime-elision

To summarise, the Rust compiler works it out using these rules, but sometimes
you have to be explicit.

1. Each parameter gets itw own lifetime parameter.

    fn foo<'a, 'b>(x: &'a i32, y: &'b i32);

2. If there is exactly one input lifetime parameter, that lifetime is assigned
   to all output lifetime parameters:

    fn foo<'a>(x: &'a i32) -> &'a i32.

3. If there are multiple input lifetime parameters, but one of them is &self or
   &mut self because this is a method, the lifetime of self is assigned to all
   output lifetime parameters.

    impl<'a> ImportantExcerpt<'a> {
        fn foo<'s, 'a, 'b>(&'s self, x: &'a i32, y: &'b i32) -> &'s i32;
    }

## Cross-compiling
Rust uses LLVM backend, so it's one-toolchain-multi-target. You can add new
targets to your `x86_64` (host) Rust toolchain like this:

    rustup target add aarch64-unknown-linux-gnu
    rustup target add x86_64-pc-windows-gnu

Make sure the aarch64 linker is installed:

    gcc-aarch64-linux-gnu

And make sure cargo and find the linker:

    [target.aarch64-unknown-linux-gnu]
    linker = "aarch64-linux-gnu-gcc"

It's non-trivial to install cross-compilers on Fedora. Do it in a container or
CI. See also: https://github.com/rust-embedded/cross
