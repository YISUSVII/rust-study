# Level 2 — Control Flow

## What you will learn

- `if` / `else`
- `match`
- `loop`, `while`, `for`
- ranges and loop control

## Simple explanation

Control flow lets your program decide and repeat behavior. Rust's `match` is exhaustive, which means the compiler forces you to handle all possible cases.

## Theory

Control flow in Rust is expression-oriented: most constructs *produce a value*, not just execute statements.

- **`if` is an expression.** `let x = if cond { 1 } else { 2 };` works because blocks evaluate to their last expression. Both arms must return the same type, and it replaces the C-style ternary operator.
- **`match` is exhaustive.** The compiler refuses to compile until every possible case is handled — no forgotten edge cases. `_` is the catch-all wildcard.
- **Three loops, three purposes.** `loop` runs until `break` (and can *return* a value via `break value;`), `while` repeats on a condition, and `for` iterates over anything that implements `Iterator`.
- **Ranges.** `1..5` excludes the end, `1..=5` includes it. Prefer `for` over manual index loops — it is safer and often faster.

## Small syntax examples

```rust
if n % 2 == 0 { "even" } else { "odd" }
```

```rust
for i in 1..=5 {
    println!("{i}");
}
```

## Common mistakes

- Infinite loops without `break`
- Forgetting `_` wildcard in `match`
- Off-by-one mistakes in ranges

## Exercises

- FizzBuzz
- Fibonacci sequence
- Prime checker

See `exercises/`.

## Hints

- Start with basic loop logic first, then refactor.
- Write helper functions for readability.

## Bonus challenges

- Add input validation and graceful retry loops.

## References

- <https://doc.rust-lang.org/book/ch03-05-control-flow.html>
- <https://doc.rust-lang.org/std/keyword.match.html>
