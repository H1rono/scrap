# RTIC触った

tags: #embedded #rust

[Preface - Real-Time Interrupt-driven Concurrency](https://rtic.rs/2/book/en/preface.html)
[rtic - Rust](https://docs.rs/cortex-m-rtic/latest/rtic/) (docs.rs)
[rtic-rs/rtic: Real-Time Interrupt-driven Concurrency (RTIC) framework for ARM Cortex-M microcontrollers](https://github.com/rtic-rs/rtic)
[RTICメモ](https://zenn.dev/ciniml/articles/rust-rtic-memo) (Zenn)

Real-Time Interrupt-driven Concurrencyの略。

## とてもつらい

と感じた。1日書いた感想ね

サンプルコード↓

- [rp-hal-boards/boards/rp-pico/examples/pico_rtic.rs at main · rp-rs/rp-hal-boards · GitHub](https://github.com/rp-rs/rp-hal-boards/blob/main/boards/rp-pico/examples/pico_rtic.rs)
- [rp-rs-stacks/rtic_blink/src/main.rs at main · H1rono/rp-rs-stacks · GitHub](https://github.com/H1rono/rp-rs-stacks/blob/main/rtic_blink/src/main.rs)
    - 前者のほぼコピペ

### マクロが多い

```rust
#[rtic::app(...)]
mod app {
    #[shared]
    struct Shared { ... }
    #[local]
    struct Local { ... }
    #[init]
    fn init(c: init::Context) ...
    ...
}
```

modにマクロが付く時点でつらい。ファイル分割を考えたとｋ
