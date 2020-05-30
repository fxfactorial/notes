# Pinning

## What is pinning?

> The metaphor is to pinning something to a corkboard, if something allows you
> to `Unpin` it then you can remove the Pin on it at any point and re-Pin it in
> a new location.

_By Nemo157 on Discord_

## Pin projections

Pinning projection is safe when:
1. `Timeout` is only Unpin when `F` is Unpin. (Ok for default auto impl)
2. `drop` never moves out of `F`. (No manual `Drop` impl and no `#[repr(packed)]`)
3. `drop` on `F` must be called before overwritten or deallocated. (No manual `Drop` impl)
4. No other operation provided for moving out `F`.

- https://github.com/rustasync/runtime/pull/70/files#diff-044e8a217c57c0f187a24281516342ecR25

## References
- https://doc.rust-lang.org/nightly/std/pin/index.html
