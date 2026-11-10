# Level 6 — Pattern Matching

## What you will learn
`match`, `if let`, `let else`, destructuring, wildcard patterns, guards.

## Simple explanation
Pattern matching lets you unpack and validate data in one clear step.

## Theory
Pattern matching is Rust's way to *take data apart* and *decide* in the same construct.

- **`match` checks structure and values.** Patterns can match literals, bind variables (`Some(x)`), destructure structs and tuples, and add extra conditions with guards (`if x > 0`).
- **Exhaustiveness as a refactoring tool.** Because the compiler checks every case, adding a new enum variant produces errors at every `match` that must be updated — refactors become guided tours instead of bug hunts.
- **Ergonomic shortcuts.** `if let` handles one interesting pattern; `let else` bails out early when a pattern fails; `while let` loops while a pattern holds.
- **Refutability.** `Some(x)` might not match (refutable); a plain variable always matches (irrefutable). `let` requires irrefutable patterns, which is why `let Some(x) = opt;` is rejected by the compiler.

## Small syntax examples
```rust
if let Some(value) = maybe { println!("{value}"); }
```

## Common mistakes
Ignoring unmatched cases, overusing `_`, and missing guard conditions.

## Exercises
- [16 — Option/Result Branching](exercises/16-option-result-branching.md)
- [17 — Enum Destructuring](exercises/17-enum-destructuring.md)
- [18 — Nested `if` to `match`](exercises/18-nested-if-to-match.md)

See `exercises/` for starters and `../solutions/06-pattern-matching/` for reference solutions.

## Hints
Prefer explicit matches before compact syntax.

## Bonus challenges
Refactor nested `if` trees into a single `match`.

## References
<https://doc.rust-lang.org/book/ch06-02-match.html>
