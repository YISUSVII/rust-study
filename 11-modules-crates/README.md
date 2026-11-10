# Level 11 — Modules, Crates and Project Structure

## What you will learn
`mod`, `pub`, `use`, crate layout, library vs binary, Cargo.toml, dependencies, workspaces.

## Simple explanation
Modules organize code; crates package code for reuse; workspaces manage multiple crates.

## Theory
Rust's module system is a hierarchy with strict, opt-in visibility — the foundation of large projects.

- **Packages, crates, modules.** A *package* (with `Cargo.toml`) builds one or more *crates* (a library and/or binaries). Inside a crate, *modules* form a tree of namespaces.
- **Everything is private by default.** `pub` exposes an item to parent modules; `pub(crate)` limits visibility to the current crate. Hiding internals lets you refactor freely without breaking users.
- **`use` brings paths into scope** — it imports no code and costs nothing at runtime.
- **Crates.io + semantic versioning.** Cargo resolves version requirements (`"1.2"` means `>=1.2.0, <2.0.0`) and locks exact versions in `Cargo.lock` so builds are reproducible.
- **Workspaces** let several related crates share one lockfile and one target directory — how real projects scale.

## Small syntax examples
```rust
mod math;
use math::add;
```

## Common mistakes
Incorrect module paths, missing `pub`, circular structure confusion.

## Exercises
- [37 — Multi-Module Project](exercises/37-multi-module-project.md)

See `exercises/` for starters and `../solutions/11-modules-crates/` for reference solutions.

## Hints
Start with a library crate, then add a binary crate.

## Bonus challenges
Create a mini workspace with shared utilities.

## References
<https://doc.rust-lang.org/book/ch07-00-managing-growing-projects-with-packages-crates-and-modules.html>
