# Level 14 — Concurrency

## What you will learn
Threads, `std::thread`, move closures, channels, mutexes, `Arc`, shared state, Send/Sync.

## Simple explanation
Concurrency lets multiple tasks make progress, but shared state must be synchronized safely.

## Theory
Rust's slogan is *fearless concurrency*: the same ownership rules that prevent memory bugs also prevent **data races** — at compile time.

- **`Send` and `Sync`** are marker traits: `Send` means safe to move to another thread, `Sync` means safe to share between threads. The compiler checks them automatically, so a data race simply does not compile.
- **Threads and `move` closures.** `std::thread::spawn` starts an OS thread; `move` transfers captured data into it; `join` waits for completion.
- **Two safe styles.** *Message passing* with channels (`mpsc`) — "don't communicate by sharing memory; share memory by communicating" — and *shared state* with `Arc<Mutex<T>>`, where holding the lock is the only way to reach the data.
- **Lock discipline matters.** Keep critical sections short, avoid holding locks across blocking calls, and know that a panicking thread *poisons* its mutex.
- **Start with message passing**; reach for shared mutable state only when profiling says so.

## Small syntax examples
```rust
let handle = std::thread::spawn(|| println!("from thread"));
handle.join().unwrap();
```

## Common mistakes
Data races via poor design, lock contention, panics on poisoned mutexes.

## Exercises
- [43 — Parallel Counter](exercises/43-parallel-counter.md)
- [44 — Producer / Consumer](exercises/44-producer-consumer.md)
- [45 — Worker Pool](exercises/45-worker-pool.md)
- [46 — Shared State Simulation](exercises/46-shared-state-simulation.md)

See `exercises/` for starters and `../solutions/14-concurrency/` for reference solutions.

## Hints
Prefer message passing before shared mutable state.

## Bonus challenges
Benchmark threaded vs single-threaded versions.

## References
<https://doc.rust-lang.org/book/ch16-00-concurrency.html>
