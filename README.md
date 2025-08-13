# HiFive1 Rev B Embedded Rust

> [!NOTE]
> Ran on my 2021 MacBook Pro M1 machine, I have not tested different OS
> configurations.

Experimenting with some starter bare metal embedded programs in Rust for the
[HiFive1 Rev B](https://www.sifive.com/boards/hifive1-rev-b).

Adapted from [`riscv-rust-quickstart`](https://github.com/riscv-rust/riscv-rust-quickstart/tree/master),
which appears to no longer be actively maintained.

## Dependencies

To build embedded programs using this template you'll need:

- Rust 1.59 or a newer toolchain. e.g. `rustup default stable`

- The `cargo generate` subcommand. [Installation
  instructions](https://github.com/ashleygwilliams/cargo-generate#installation).

- `rust-std` components (pre-compiled `core` crate) for the RISC-V target. Run:

  ```bash
  rustup target add riscv32imac-unknown-none-elf
  ```

- ~[RISC-V toolchain for SiFive boards](https://static.dev.sifive.com/dev-tools/riscv64-unknown-elf-gcc-8.1.0-2019.01.0-x86_64-linux-ubuntu14.tar.gz)~
  - Instead, I was able to get by with just `gdb` via Homebrew:

  ```bash
  brew install gdb
  ```

- [Segger JLinkGDBServer](https://www.segger.com/downloads/jlink/) &rarr; debug
  probe that will connect to the running `gdb` process when we run a program

## Running

1. In one terminal:

```sh
LinkGDBServer -device FE310 -if JTAG -speed 4000 -port 3333 -nogui
```

2. Build the project or a single example:

```bash
cargo build
# or
cargo build --example leds_blink
```

3. Run the template application or one of the examples.

```bash
cargo run
# or
cargo run --example leds_blink
```
