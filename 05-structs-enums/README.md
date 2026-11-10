# Level 5 — Structs and Enums

## What you will learn
Structs, tuple structs, methods, associated functions, enums, `Option`, `Result`.

## Simple explanation
Structs model data; enums model a value that can be one of multiple variants.

## Theory
Structs and enums are how you model a domain: structs are *product types* (a value has all of these fields), enums are *sum types* (a value is exactly one of these variants).

- **`impl` blocks** attach behavior to data. Methods take `self` (by value), `&self` (read-only), or `&mut self` (mutating). Functions without `self` — like `String::from` — are *associated functions*, used as constructors and helpers.
- **`Option<T>` replaces null.** Instead of any reference secretly being null, absence is explicit: `Some(value)` or `None`. The compiler forces you to handle both cases.
- **`Result<T, E>`** does the same for failure: `Ok(value)` or `Err(error)` — you will meet it constantly from Level 8 onwards.
- **Model invalid states away.** A well-designed enum (`enum OrderState { Placed, Paid, Shipped }`) makes illegal states unrepresentable, turning bugs into compile errors.

## Small syntax examples
```rust
struct User { name: String, age: u8 }
enum TrafficLight { Red, Yellow, Green }
```

## Common mistakes
Forgetting `impl` blocks, overusing mutable state, not matching all enum variants.

## Exercises
- [11 — User Model](exercises/11-user-model.md)
- [12 — Rectangle Model](exercises/12-rectangle-model.md)
- [13 — Bank Account](exercises/13-bank-account.md)
- [14 — Order State Machine](exercises/14-state-machine.md)
- [15 — Traffic Light](exercises/15-traffic-light.md)

See `exercises/` for starters and `../solutions/05-structs-enums/` for reference solutions.

## Hints
Use methods to keep behavior near data.

## Bonus challenges
Implement validation logic with `Result`.

## References
<https://doc.rust-lang.org/book/ch05-00-structs.html>
<https://doc.rust-lang.org/book/ch06-00-enums.html>
