# Rust Features

## Cargo.toml
1. Features can't be named the same as one of their dependencies.
2. The list in the `[features]` tag lists what their dependencies are.
3. Tag each dependency with `optional = true`.

```toml
[features]
default = ["middleware-logger"]
middleware-logger = ["log"]

[dependencies]
log = { version = "0.4.7", optional = true }
```

## Rust Usage
```rust
mod middleware {
#[cfg(feature = "middleware-logger")]
    pub mod logger;
}
```

Or using `if` statements:
```rust
if cfg!(feature = "middleware-logger") {
    pub mod logger;
}
```

## Forwarding Features
It's possible to expose dependency feature flags from your own crate:
```rust
[features]
curl-static = ["url/static-curl"]
```

## Enable dependencies only on specific platforms
```rust
[target.'cfg(any(target_os = "linux", target_os = "macos", target_os="windows"))'.dependencies]
fs2 = "0.4.3"
```
