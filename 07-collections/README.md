# Level 7 — Collections and Strings

## What you will learn
`Vec<T>`, `String`, `HashMap`, `HashSet`, iteration, updates, ownership in collections.

## Simple explanation
Collections store multiple values and often own their contents, so ownership rules still apply.

## Theory
Standard collections live on the heap and *own* their contents, so ownership and borrowing apply inside them too.

- **`Vec<T>`** is a growable, contiguous array: O(1) push and indexing, cache-friendly, the default "list" choice.
- **`String` is UTF-8.** It wraps a `Vec<u8>`; because one character can be 1–4 bytes, indexing a `String` by position is deliberately not allowed. Use `chars()`, `bytes()`, or slices instead.
- **`HashMap<K, V>`** stores key→value pairs with average O(1) lookup. The `entry` API (`counts.entry(word).and_modify(..).or_insert(0)`) avoids double lookups and redundant clones.
- **Borrowing from collections.** `map.get(&key)` returns `Option<&V>` — a borrow tied to the map, so you cannot mutate the map while that borrow lives. Clone or restructure when needed.
- **Choose by access pattern:** `Vec` for ordered sequences, `HashMap` for lookup by key, `HashSet` for membership tests, `VecDeque` for queues.

## Small syntax examples
```rust
use std::collections::HashMap;
let mut counts = HashMap::new();
counts.insert("rust", 1);
```

## Common mistakes
Index out of bounds, cloning unnecessarily, misunderstanding borrowed keys.

## Exercises
- [19 — Word Frequency](exercises/19-word-frequency.md)
- [20 — Grade Tracker](exercises/20-grade-tracker.md)
- [21 — Duplicate Remover](exercises/21-duplicate-remover.md)
- [22 — Inventory](exercises/22-inventory.md)
- [23 — Text Analyzer](exercises/23-text-analyzer.md)

See `exercises/` for starters and `../solutions/07-collections/` for reference solutions.

## Hints
Use iterators and entry APIs (`entry`, `or_insert`).

## Bonus challenges
Optimize memory allocations and avoid redundant clones.

## References
<https://doc.rust-lang.org/book/ch08-00-common-collections.html>
