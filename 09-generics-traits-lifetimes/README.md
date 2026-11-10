# Level 9 — Generics, Traits and Lifetimes

## What you will learn
Generic functions/structs, traits, trait bounds, `where`, `impl Trait`, lifetimes.

## Simple explanation
Generics remove duplication, traits describe shared behavior, and lifetimes explain reference validity.

## Theory
Three tools fight duplication without giving up safety or speed.

- **Generics** let one definition work for many types. Rust *monomorphizes*: at compile time it generates a specialized copy per concrete type, so generics have **zero runtime cost** — no boxing, no virtual calls.
- **Traits define shared behavior**, like interfaces with superpowers: they can be implemented for types you didn't write, provide default methods, and act as bounds (`T: Display`) or as trait objects (`&dyn Display`).
- **`where` clauses** keep complex bounds readable; `impl Trait` in argument or return position is shorthand for simple generics.
- **Lifetimes describe how long references stay valid.** They change nothing at runtime — they give the compiler the relationships it needs to prove no reference dangles. When you annotate `fn first<'a>(a: &'a str, b: &'a str) -> &'a str`, you document that the result lives as long as the inputs.
- **Elision rules** cover the common cases, so simple functions need no lifetime annotations at all.

## Small syntax examples
```rust
fn max<T: Ord>(a: T, b: T) -> T { if a > b { a } else { b } }
```

## Common mistakes
Overconstraining bounds and returning references without valid lifetime relationships.

## Exercises
- [28 — Generic Max](exercises/28-generic-max.md)
- [29 — Printable Trait](exercises/29-printable-trait.md)
- [30 — Shape Trait](exercises/30-shape-trait.md)
- [31 — Repository Abstraction](exercises/31-repository-abstraction.md)
- [32 — Reference-Returning APIs](exercises/32-reference-returning-apis.md)

See `exercises/` for starters and `../solutions/09-generics-traits-lifetimes/` for reference solutions.

## Hints
Write constraints only when needed.

## Bonus challenges
Combine multiple trait bounds with `where`.

## References
<https://doc.rust-lang.org/book/ch10-00-generics.html>
