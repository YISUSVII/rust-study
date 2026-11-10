# Level 8 — Error Handling

## What you will learn
`panic!`, `Result`, `Option`, `unwrap`, `expect`, `?`, custom errors.

## Simple explanation
Rust distinguishes recoverable errors (`Result`) from unrecoverable failures (`panic!`).

## Theory
Rust has no exceptions. Failure is a *value* you can inspect, pass around, and are forced to acknowledge.

- **`Result<T, E>` for recoverable errors** — parsing, I/O, network. Callers decide: retry, use a default, or propagate.
- **`panic!` for bugs** — violated invariants, "this should never happen". A panic unwinds the thread; it is not a control-flow tool.
- **The `?` operator** unwraps `Ok` or returns the `Err` early, converting error types when possible. It keeps fallible pipelines readable.
- **`unwrap` / `expect` mean "I promise this can't fail".** Fine in tests and prototypes; in production code prefer handling errors, or at least `expect` with a clear reason.
- **Libraries vs applications.** Libraries return rich, typed errors (custom enums; the `thiserror` crate helps). Applications want context and reporting (`anyhow` helps).
- **`Option` vs `Result`:** use `Option` when absence is not an error (a lookup miss), `Result` when the caller needs to know *why* it failed.

## Small syntax examples
```rust
fn parse_num(s: &str) -> Result<i32, std::num::ParseIntError> { s.parse() }
```

## Common mistakes
Overusing `unwrap`, swallowing context, and returning vague error types.

## Exercises
- [24 — File Reading](exercises/24-file-reading.md)
- [25 — Parsing](exercises/25-parsing.md)
- [26 — Data Validation](exercises/26-data-validation.md)
- [27 — Custom Errors](exercises/27-custom-errors.md)

See `exercises/` for starters and `../solutions/08-error-handling/` for reference solutions.

## Hints
Prefer `?` and meaningful error messages.

## Bonus challenges
Model domain-specific errors with enums.

## References
<https://doc.rust-lang.org/book/ch09-00-error-handling.html>
