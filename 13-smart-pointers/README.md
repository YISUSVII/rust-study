# Level 13 — Smart Pointers

## What you will learn
`Box<T>`, `Rc<T>`, `Arc<T>`, `RefCell<T>`, interior mutability, `Deref`, `Drop`.

## Simple explanation
Smart pointers add ownership behaviors like shared ownership or runtime borrow checking.

## Theory
Smart pointers are structs that behave like references while adding ownership superpowers, via the `Deref` and `Drop` traits.

- **`Box<T>`** — heap allocation with a single owner. Use it for recursive types (a type containing itself needs indirection to have a known size) and for moving large data cheaply.
- **`Rc<T>`** (reference counted) — multiple owners within *one thread*; the value drops when the last `Rc` goes away. `Rc<RefCell<T>>` is the classic "shared mutable state" combo for GUIs and graphs.
- **`Arc<T>`** — the thread-safe `Rc` (atomic counting), required when ownership crosses threads.
- **Interior mutability (`RefCell<T>`, `Mutex<T>`)** moves the borrow rules from compile time to runtime: you may mutate through a shared reference, but violations *panic* instead of failing to compile.
- **`Weak<T>`** breaks `Rc` reference cycles — otherwise two structures pointing at each other would leak forever.
- **Rule of thumb:** start with plain ownership; add `Box` for indirection, `Rc`/`Arc` only when ownership is genuinely shared.

## Small syntax examples
```rust
use std::rc::Rc;
let shared = Rc::new(String::from("data"));
```

## Common mistakes
Reference cycles, unnecessary shared ownership, misusing `RefCell`.

## Exercises
- [40 — Box Recursive List](exercises/40-box-recursive-list.md)
- [41 — Rc + RefCell Shared State](exercises/41-rc-refcell-shared-state.md)
- [42 — Weak Tree](exercises/42-weak-tree.md)

See `exercises/` for starters and `../solutions/13-smart-pointers/` for reference solutions.

## Hints
Pick the smallest abstraction that fits your ownership needs.

## Bonus challenges
Prevent or detect `Rc` cycles in graph-like data.

## References
<https://doc.rust-lang.org/book/ch15-00-smart-pointers.html>
