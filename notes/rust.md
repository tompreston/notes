# Rust
Move, Copy, Clone. These rust docs give the best explaination:

    std::marker::Copy
    std::clone::Clone

By default, variables have "move" semantics unless they derrive a Copy
implementation.

Clone is a bit more involved - sometimes a data structure references data on
the heap so it needs a "deep" copy (which is what clone is).
