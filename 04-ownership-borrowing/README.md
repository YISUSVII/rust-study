# Level 4 — Ownership and Borrowing

## What you will learn

- Stack vs heap
- Ownership, moves, copies, cloning
- References and borrowing
- Mutable borrowing and borrowing rules
- Slices and string slices

## Simple explanation

Ownership is Rust's core memory-safety model. Every value has one owner, and when ownership moves, the previous binding is no longer valid. Borrowing lets you reference data without taking ownership.

## Theory

Ownership is how Rust guarantees memory safety **without a garbage collector**. The compiler enforces three rules: each value has exactly one owner; the value is dropped when its owner goes out of scope; ownership can move or be borrowed, never silently shared.

- **Stack vs heap.** Stack data has a known fixed size and is freed automatically; heap data (like `String`) grows at runtime and must be freed exactly once. Ownership tracks *who* frees it — no `free`, no GC pauses, no leaks from forgotten cleanup.
- **Move semantics.** Assigning a heap value to another binding *moves* ownership — the old binding becomes invalid. Types that are cheap to duplicate (`i32`, `bool`, ...) implement `Copy` and are copied instead.
- **Borrowing.** `&T` reads without owning; `&mut T` mutates without owning. At any moment you may have *either* many `&T` *or* exactly one `&mut T` — never both. This single rule eliminates data races at compile time.
- **No dangling references.** The compiler proves every reference outlives the data it points to; returning `&` to a local variable is a compile error, not a runtime crash.
- **Slices.** `&str` and `&[T]` are views into data owned by someone else — the idiomatic way to accept "any string-like or sequence-like" input.

## Small syntax examples

```rust
fn len(s: &String) -> usize {
    s.len()
}

fn main() {
    let text = String::from("rust");
    println!("{}", len(&text));
}
```

```rust
fn first_word(s: &str) -> &str {
    match s.find(' ') {
        Some(i) => &s[..i],
        None => s,
    }
}
```

## Common mistakes

- Using a moved value after ownership transfer
- Creating multiple mutable borrows simultaneously
- Returning references to local values

## Exercises

- Fix move vs clone compiler error
- Update a `String` via mutable borrowing
- Return string slices safely

See `exercises/`.

## Hints

- Read compiler errors fully; they usually explain the exact rule violated.
- Prefer borrowing (`&T` / `&mut T`) before cloning.

## Bonus challenges

- Refactor ownership-heavy code to reduce clones.

## Important compiler errors to understand

- `E0382`: use of moved value
- `E0502`: cannot borrow as mutable because it is also borrowed as immutable
- `E0515`: cannot return reference to local variable

## References

- <https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html>
- <https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html>
- <https://doc.rust-lang.org/book/ch04-03-slices.html>
