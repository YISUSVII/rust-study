# Level 1 — Rust Fundamentals

## What you will learn

- Variables with `let`
- Mutability, constants, and shadowing
- Primitive types: integers, floats, booleans, chars
- Compound types: tuples and arrays

## Simple explanation

Rust variables are immutable by default. You explicitly opt into mutability with `mut`. Rust's type system helps catch mistakes early and encourages explicit intent.

## Theory

Rust is **statically typed**: every value has a type known at compile time, and the compiler checks all operations before the program runs. Type inference means you rarely write types explicitly, but they always exist.

- **Immutability by default.** A `let` binding cannot change unless you add `mut`. This removes a whole class of bugs (accidental state changes) and makes code easier to reason about.
- **Constants vs variables.** `const` values are computed at compile time, always need a type annotation, and are inlined wherever they are used.
- **Shadowing.** Re-declaring `let x = ...` creates a *new* binding that may even change type. Unlike `mut`, shadowing keeps the value immutable between redeclarations.
- **Scalar types.** Integers (`i32`, `u64`, ...), floats (`f64`), `bool`, and `char` (a 4-byte Unicode scalar, not a single byte). If you don't pick an integer type, Rust defaults to `i32`.
- **Compound types.** Tuples group values of mixed types with fixed size; arrays hold same-typed values with fixed size, stored on the stack.
- **Integer overflow** panics in debug builds and wraps in release builds — an example of Rust preferring correctness while you develop.

## Small syntax examples

```rust
let x = 10;
let mut y = 5;
y += 1;
const MAX_USERS: u32 = 100;
let y = y * 2; // shadowing
```

```rust
let t: (i32, f64, char) = (42, 3.14, 'R');
let arr = [1, 2, 3, 4];
```

## Common mistakes

- Trying to mutate a non-`mut` variable
- Confusing shadowing with mutation
- Using the wrong numeric type for calculations

## Exercises

- Temperature converter
- Rectangle area calculator
- Basic calculator
- Unit converter

See `exercises/` for detailed prompts.

## Hints

- Parse input safely and return useful errors.
- Keep functions small and focused.

## Bonus challenges

- Add unit conversion menus.
- Support decimal inputs and better formatting.

## References

- <https://doc.rust-lang.org/book/ch03-00-common-programming-concepts.html>
- <https://doc.rust-lang.org/std/primitive/>
