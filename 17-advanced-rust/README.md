# Level 17 — Advanced Rust

## What you will learn
Advanced traits, associated types, trait objects, dynamic dispatch, unsafe Rust, raw pointers, FFI concepts, pinning basics.

## Simple explanation
Advanced Rust balances zero-cost abstractions with controlled low-level power when needed.

## Theory
Advanced features share one theme: precise control over abstraction and memory when the defaults are not enough.

- **Associated types vs generics.** `trait Iterator { type Item; }` — one implementation picks exactly one `Item`, while generic parameters allow many implementations. Associated types keep APIs like `Iterator` clean.
- **Trait objects (`&dyn Trait`, `Box<dyn Trait>`)** enable *dynamic dispatch*: different concrete types behind one interface, called through a vtable. You trade static optimization for runtime flexibility (heterogeneous collections, plugin systems).
- **Static vs dynamic dispatch.** Generics monomorphize (faster, bigger binary); `dyn` dispatches at runtime (smaller, flexible). Choose per use case.
- **`unsafe` is a scoped contract**, not a chaos switch. Inside it you may dereference raw pointers, call foreign functions, and rely on invariants the compiler cannot check — but *you* uphold safety. Best practice: tiny `unsafe` internals behind safe public APIs, with documented invariants.
- **FFI and pinning.** `extern "C"` connects Rust to C libraries and other languages; `Pin` guarantees self-referential data never moves — the backbone of async internals.

## Small syntax examples
```rust
trait IteratorLike { type Item; }
```

## Common mistakes
Using `unsafe` without clear invariants and poor encapsulation.

## Exercises
Isolated unsafe labs, trait-object APIs, advanced lifetime reasoning tasks.

## Hints
Document invariants around unsafe blocks.

## Bonus challenges
Wrap unsafe internals in safe public APIs.

## References
<https://doc.rust-lang.org/book/ch19-00-advanced-features.html>
