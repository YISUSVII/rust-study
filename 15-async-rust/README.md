# Level 15 — Async Rust

## What you will learn
`async`, `await`, futures, Tokio, async tasks, concurrent execution, basic HTTP requests.

## Simple explanation
Async handles many waiting tasks efficiently without one OS thread per task.

## Theory
Async Rust runs thousands of waiting tasks on a few OS threads through *cooperative* scheduling.

- **A future is an inert state machine.** `async fn` compiles to a type implementing `Future`; calling it does *nothing* until something polls it. `await` yields control back to the scheduler when work cannot progress yet.
- **The runtime drives everything.** Tokio (the de-facto standard) polls futures, wakes them when I/O is ready, and schedules tasks across a thread pool. No runtime, no execution.
- **Concurrency ≠ parallelism.** Threads run code simultaneously; async interleaves *waiting* tasks on few threads. For CPU-heavy work you still want threads (`tokio::task::spawn_blocking`).
- **Never block the async thread.** A blocking call (`std::thread::sleep`, synchronous file I/O) stalls every task on that thread — use `tokio::time::sleep` and async APIs instead.
- **Composition.** `tokio::join!` and `tokio::spawn` run futures concurrently; timeouts, retries, and cancellation compose cleanly because futures are values.

## Small syntax examples
```rust
async fn hello() { println!("hello async"); }
```

## Common mistakes
Blocking inside async code and confusing async concurrency with threads.

## Exercises
- [47 — Async Timer](exercises/47-async-timer.md)
- [48 — Concurrent Requests](exercises/48-concurrent-requests.md)
- [49 — Async API Client](exercises/49-async-api-client.md)

See `exercises/` for starters and `../solutions/15-async-rust/` for reference solutions.

## Hints
Use Tokio runtime and avoid blocking calls in async contexts.

## Bonus challenges
Add retries and timeouts to async clients.

## References
<https://rust-lang.github.io/async-book/>
