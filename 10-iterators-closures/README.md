# Level 10 — Closures and Iterators

## What you will learn
Closures, Iterator trait, `map`, `filter`, `fold`, `collect`, `enumerate`, `zip`.

## Simple explanation
Iterators transform data lazily and compositionally; closures capture surrounding context.

## Theory
Closures and iterators are Rust's functional core — expressive *and* zero-cost.

- **Closures capture their environment automatically**: by reference, mutably, or by value (with `move`). Each closure implements one or more of the `Fn` / `FnMut` / `FnOnce` traits, which is how APIs declare what kind of closure they need.
- **Iterators are lazy.** `map` / `filter` / `take` build a *description* of work; nothing happens until a consumer (`collect`, `sum`, `for`) pulls values through the chain.
- **Zero-cost chains.** The compiler inlines iterator chains into loops as tight as hand-written ones — you get declarative style without the runtime price.
- **`collect()` is the bridge** back to collections; its target type (often via the turbofish `collect::<Vec<_>>()`) decides what gets built.
- **Prefer iterators over manual loops** when transforming data; keep explicit loops for side-effect-heavy or early-exit logic.

## Small syntax examples
```rust
let sum: i32 = vec![1,2,3].into_iter().map(|n| n * 2).sum();
```

## Common mistakes
Collecting too early, ownership confusion in closures, unreadable chains.

## Exercises
- [33 — Data Transforms](exercises/33-data-transforms.md)
- [34 — User Filtering](exercises/34-user-filtering.md)
- [35 — Stats](exercises/35-stats.md)
- [36 — Word Processing](exercises/36-word-processing.md)

See `exercises/` for starters and `../solutions/10-iterators-closures/` for reference solutions.

## Hints
Build chains step by step, then refactor.

## Bonus challenges
Implement custom iterator adaptors.

## References
<https://doc.rust-lang.org/book/ch13-00-functional-features.html>
