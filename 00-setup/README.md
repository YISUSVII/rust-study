# Level 0 — Setup

## What you will learn

- Installing Rust with `rustup` on Windows, macOS, and Linux
- Using `rustc` and `cargo`
- Creating and running your first project
- Trying Rust online with the Rust Playground
- Running quality tools: `cargo fmt` and `cargo clippy`

## Simple explanation

Rust projects are usually built with Cargo, Rust's official package manager and build tool. `rustc` compiles a single file directly, while Cargo helps manage complete projects. Everything is installed and kept up to date through `rustup`, the official toolchain manager.

## Official websites

- Rust homepage: <https://www.rust-lang.org/>
- Install page: <https://www.rust-lang.org/tools/install>
- `rustup` installer: <https://rustup.rs/>
- The Rust Book: <https://doc.rust-lang.org/book/>
- Standard library docs: <https://doc.rust-lang.org/std/>
- Cargo docs: <https://doc.rust-lang.org/cargo/>
- Package registry: <https://crates.io/>
- Online playground: <https://play.rust-lang.org/>

## Install on Windows

1. Download `rustup-init.exe` from <https://rustup.rs/> (or the install page above).
2. Run it and choose option `1` (*Proceed with standard installation*).
3. If prompted, install the **Microsoft C++ Build Tools** first (Visual Studio Build Tools with the "Desktop development with C++" workload). Rust's default Windows toolchain (`x86_64-pc-windows-msvc`) needs them to link programs.
4. Close and reopen the terminal so `PATH` is refreshed.

PowerShell alternative (the C++ Build Tools are still required):

```powershell
winget install Rustlang.Rustup
```

## Install on macOS

Install the Xcode Command Line Tools (needed for the linker), then run the official `rustup` script and pick option `1`:

```bash
xcode-select --install
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"
```

Restart the terminal afterwards (or keep the `source` line above in your shell profile).

## Install on Linux

Make sure a C linker and build tools exist, then run the official `rustup` script and pick option `1`:

```bash
# Debian / Ubuntu:
sudo apt update && sudo apt install build-essential curl
# Fedora:
sudo dnf install gcc curl
# Arch:
sudo pacman -S --needed base-devel curl

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"
```

Restart the terminal afterwards.

## Verify your setup

Run these in a **new** terminal. Each command should print a version, not an error:

```bash
rustc --version    # the compiler
cargo --version    # the build tool and package manager
rustup --version   # the toolchain manager
rustup show        # installed toolchains and targets
```

Keep the toolchain current with:

```bash
rustup update
```

## Try Rust without installing: the Playground

You can run Rust in the browser at <https://play.rust-lang.org/> — nothing to install:

1. Open the link and edit the code in the editor.
2. Click **Run** (or press `Ctrl+Enter` / `Cmd+Enter`) and read the output below.
3. Use the top-right menus for `rustfmt`, `clippy`, and debug/release modes.

The Playground is perfect for testing small snippets, but install Rust locally for this course: the exercises use files, projects, and Cargo commands.

## Your first local project

```bash
cargo new hello_rust
cd hello_rust
cargo run               # build and run
cargo check             # fast check, no binary produced
cargo build             # debug build -> target/debug/
cargo build --release   # optimized build
cargo fmt               # format the code
cargo clippy            # lints and improvement suggestions
```

You can also compile a single file without Cargo:

```bash
rustc main.rs
./main        # on Windows: .\main.exe
```

```rust
fn main() {
    println!("Hello, Rust!");
}
```

## Common mistakes

- Not restarting the terminal after `rustup` installation
- Skipping the C++ Build Tools (Windows) or Xcode CLT (macOS), causing linker errors
- Running `cargo run` outside a Cargo project folder
- Ignoring `cargo fmt` / `cargo clippy` warnings early

## Exercises

1. **Install and verify**: Install Rust and confirm `rustc --version` and `cargo --version` work.
2. **Playground warm-up**: Run `println!("Hello from the playground");` at <https://play.rust-lang.org/>.
3. **First project**: Create `hello_rust` and run it locally.
4. **Tooling drill**: Run `cargo check`, `cargo fmt`, and `cargo clippy`.

## Hints

- `cargo new <project_name>` creates a complete starter project.
- `cargo check` is faster than `cargo build` while iterating.
- `rustup doc --book` opens the Rust Book offline.

## Bonus challenge

Print your name and learning goal in the Hello World app.

## References

- <https://www.rust-lang.org/tools/install>
- <https://rustup.rs/>
- <https://play.rust-lang.org/>
- <https://doc.rust-lang.org/book/ch01-00-getting-started.html>
- <https://doc.rust-lang.org/cargo/>
