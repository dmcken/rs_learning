# Mono repo scaffolding

Problem definition: How to setup a mono repo of multiple binary and library projects.

## Steps

```bash
cd <home>
mkdir libs
mkdir services
```

```bash
cd <home>/libs
cargo new utils --libs
```

```bash
cd <home>/services
cargo new client --bin
cargo new server --bin
```

Create / Edit `Cargo.toml` in the root directory. Ensure it has the following:

```toml
[workspace]
members = [
    "services/server",
    "services/client",
]

[workspace.dependencies]
utils = { path = "libs/utils" }
```

In client's `Cargo.toml` you can now add the following to make it available to that project.

```toml
[dependencies]
utils = { workspace = true }
```

## References

* https://doc.rust-lang.org/cargo/guide/project-layout.html - General layout of a cargo layout.
* https://doc.rust-lang.org/cargo/reference/workspaces.html
* https://earthly.dev/blog/rust-monorepo/

