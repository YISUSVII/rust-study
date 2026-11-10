# Level 3 — Functions

## What you will learn

- Function declarations
- Parameters and return values
- Expressions vs statements
- Scope and reuse

## Simple explanation

Functions help organize logic into reusable units. In Rust, the last expression of a block can be an implicit return value.

## Theory

Functions are the basic unit of reuse, and Rust's design nudges you toward small, predictable ones.

- **Statements vs expressions.** Statements (`let x = 5;`, any line ending in `;`) do something and return nothing. Expressions evaluate to a value. A function body ends in an optional final expression — that expression is the return value; adding `;` turns it into a statement and breaks the return.
- **Types are mandatory in signatures.** Callers must be able to check a function without reading its body, so every parameter and the return type are explicit. This is intentional documentation.
- **Early returns.** `return expr;` exits immediately; idiomatic Rust uses it for guard clauses, keeping the final expression as the "happy path".
- **Conventions.** `snake_case` names, functions that do one thing, and pure functions (same input → same output, no side effects) wherever practical.

## Small syntax examples

```rust
fn add(a: i32, b: i32) -> i32 {
    a + b
}
```

```rust
fn main() {
    let result = add(2, 3);
    println!("{result}");
}
```

## Common mistakes

- Adding `;` to the final expression unintentionally
- Returning the wrong type
- Overloading one function with too many responsibilities

## Exercises

- Break a mini calculator into reusable functions

See `exercises/`.

## Hints

- Name functions by behavior (`calculate_area`, `to_celsius`).
- Keep each function doing one thing.

## Bonus challenges

- Write unit tests for pure functions.

## References

- <https://doc.rust-lang.org/book/ch03-03-how-functions-work.html>
