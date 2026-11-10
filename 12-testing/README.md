# Level 12 — Testing

## What you will learn
Unit tests, integration tests, `#[test]`, assertions, `cargo test`, test organization.

## Simple explanation
Tests lock expected behavior and make refactoring safer.

## Theory
Tests in Rust are ordinary code, compiled and run by a built-in harness — no external framework needed.

- **`#[test]` marks a test; `cargo test` discovers them and runs them in parallel** across threads. Shared mutable state between tests is a design smell.
- **Assertions as contracts.** `assert!` checks conditions; `assert_eq!` / `assert_ne!` compare values and print both sides on failure. A good failure message tells you what *should* have happened.
- **`#[should_panic]`** verifies error paths; tests returning `Result` can use `?`.
- **Unit tests** live beside the code (`#[cfg(test)] mod tests`) and can touch private items; **integration tests** in `tests/` use only the public API — they test what users experience.
- **The red–green–refactor loop:** write a failing test, make it pass, then clean up. Tests are the safety net that makes fearless refactoring possible.

## Small syntax examples
```rust
#[test]
fn adds_two_numbers() { assert_eq!(2 + 2, 4); }
```

## Common mistakes
Testing implementation details, weak assertion messages, slow test setup.

## Exercises
- [38 — Unit Tests](exercises/38-unit-tests.md)
- [39 — Table-Driven Tests](exercises/39-table-driven-tests.md)

See `exercises/` for starters and `../solutions/12-testing/` for reference solutions.

## Hints
Prefer deterministic tests with clear names.

## Bonus challenges
Use table-driven patterns and error-case tests.

## References
<https://doc.rust-lang.org/book/ch11-00-testing.html>
