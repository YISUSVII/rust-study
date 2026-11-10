# Level 16 — Macros

## What you will learn
`macro_rules!`, declarative macros, standard macros, procedural macro basics.

## Simple explanation
Macros generate Rust code, reducing repetitive patterns.

## Theory
Macros are **compile-time code generation**: they receive tokens and expand into ordinary Rust before type checking.

- **`macro_rules!` (declarative macros)** pattern-match the tokens you pass in and substitute a template — think "a `match` statement for syntax". `vec![1, 2, 3]` and `println!` are built this way.
- **Macros ≠ functions.** They can take variable argument counts and generate definitions, and their arguments are not evaluated normally. The cost: they are harder to read, debug, and document — use them when functions or generics *cannot* express the pattern.
- **Hygiene.** Names introduced inside a macro do not leak out and collide with caller variables — a safety feature most macro systems lack.
- **Procedural macros** (`derive`, attribute, and function-like) run real Rust code at compile time over the parsed syntax tree; `#[derive(Debug)]` is the everyday example.
- **Debugging tip:** `cargo expand` shows the generated code when an expansion surprises you.

## Small syntax examples
```rust
macro_rules! say_hi { () => { println!("hi"); } }
```

## Common mistakes
Overengineering macros and unclear expansion behavior.

## Exercises
- [50 — Declarative Macros](exercises/50-declarative-macros.md)
- [51 — Repetition Macros](exercises/51-repetition-macros.md)

See `exercises/` for starters and `../solutions/16-macros/` for reference solutions.

## Hints
Start with pattern matching tokens and small expansions.

## Bonus challenges
Inspect macro expansion with tooling.

## References
<https://doc.rust-lang.org/book/ch19-06-macros.html>
